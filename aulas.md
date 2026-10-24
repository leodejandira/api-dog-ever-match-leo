# Aula dia 23/10

# **Instalando dependencias**

- nmp i no terminal, dentro da pasta


- Dentro de *models*, temos a modelagem de dados.
usamos o sqlite 3, banco local

- Dentro do *middlewares*, temos a token de autenticação do usurario. jwt (json web token). Podemos por autenticate em rotas, que validam se o jwt está sendo usado (autentica é uma func). É uma funcao criada por nós, e nesse projeto, usamos um lib para isso no mid

- Nas extensoes, instale o thunder client, que é para testar aplicações.

- Para rodar o projeto, temos que rodar o *npm run start*

- Depois, clique em new request no thunder client ou instale o bruno. nese caso, usaremos o bruno

- Clique em new colection e dê um nome, salve numa pasta e cria a collection

- Clqiue no +, selecione http, eagora podemos chamar endpoints

- Digite http://localhost:3000/dogs/getAllDogs no get. se tiver autemticacao, vai negar

- Cria uma nova requisição, e use o metodo post para autenticar: http://localhost:3000/auth/login. clique em body, e em json

- Adicione esse json:

{
  "email": "teste@gmail.com",
  "password": "1234"
}

- Copie o token, e pesquise jwt.io, cole o token, e veje a datade expira~c"ao, email, id e data e inicio. a data está em unix

- Por no meclatura, em api profissional, recebmos dois token: accsses e refresh. Accsses para entrar, de uns 15 min, e o refresh é para quando o token de accsses expirar. e apartir daí, o token de resresh tem um tempo maior de expiração

- Com a api rorando, crie outro terminal. no google,  pesquise reactive native, va em get start, copie e rode o ocmando:

npx create-expo-app@latest

- Intale usando o sdk 55

ENTRE NA PASTA E DE UM CODE .

rode na pasta no app, npm install axios
depos, assim como na api, rode no app o nmp run start, e entre na versao web


**abra o cõdigo, vai no index e edite:**


cria a chaamda da api, de forma assincrona, para evitar problemas de lentidao 

chame o métogo get, echame as imagens dos cachorros, e adicione o m~etod then para pegar a resposta da api 

```jsx
import axios from 'axios';
import { useEffect, useState } from 'react';
import { Image, View } from "react-native";


export default function HomeScreen() {

  const [valorApi, setValorApi] = useState([])


  const chamaApi = async () => {
    try {
      const resp = await axios.get('http://localhost:3000/dogs/getAllDogs')
      setValorApi(resp.data)
    } catch (error) {
      console.log('Erro ao chamar API:', error)
    }
  }

  useEffect (() => {
    chamaApi()
  }, [])



  return (
    <View>
      <Image
        source={{ uri: valorApi[0]?.image[0] }}
        style={{
          height: 300,
          width: 300,
        }}
      />
    </View>
  );
}
```



agora, vams adicoianr os boteos de sim e nao, vermelho e verde
```jsx
      <TouchableOpacity
        style={{
          height: 50,
          width: 50,
          backgroundColor: 'red',
        }}
      />

      <TouchableOpacity
        style={{
          height: 50,
          width: 50,
          backgroundColor: 'green',
        }}
      />
```

- agora vamos por a logica do tinder. conforme vc dá nao, elimina da lista. a porxima da lista sempre é primeira, e é a que enxergamos. caso vc de sim, vai para outra lista, chamada match







