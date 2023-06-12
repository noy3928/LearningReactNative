## Learning Point

- TouchableOpactiy : 터치가 가능한 투명한 영역을 만들어주는 컴포넌트.
- KeyboardAvoidingView : 키보드가 올라오면서 화면이 가려지는 것을 방지해주는 컴포넌트.
  - behavior : 키보드가 올라올 때 어떻게 행동할지 결정하는 속성.
    - padding : 키보드가 올라오면 화면을 밀어줌.
    - height : 키보드가 올라오면 화면을 밀어줌.
    - position : 키보드가 올라오면 화면을 밀어줌.
- Keyboard.dismiss() : 키보드를 내려주는 함수.
  - 키보드가 올라와있는 상태에서 다른 곳을 터치하면 키보드가 내려가도록 구현.

<br>

## React Navigation

- RN에서 라우팅을 하기 위한 라이브러리이다.
- NavigationContainer로 전체 app을 감싸줘야한다.[link](https://reactnavigation.org/docs/getting-started/#wrapping-your-app-in-navigationcontainer)
- RN에는 웹브라우저처럼 history가 없기 때문에 history를 관리해주는 역할을 하는 것이 react navigation이다.
  - 화면 전환과, 탐색 기록의 기능을 제공한다.
  - 웹과의 차이점은 native앱에서 기대할 수 있는 제스처와 애니메이션을 제공해준다는 것이다.

### Hello React Navigation

- App 화면 세팅방법

```js
// In App.js in a new project

import * as React from "react"
import { View, Text } from "react-native"
import { NavigationContainer } from "@react-navigation/native"
import { createNativeStackNavigator } from "@react-navigation/native-stack"

function HomeScreen() {
  return (
    <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
      <Text>Home Screen</Text>
    </View>
  )
}

const Stack = createNativeStackNavigator()

function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={HomeScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  )
}

export default App
```

- 경로지정하기 : Screen 컴포넌트를 통해서 경로를 지정할 수 있다.
