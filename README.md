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

<br>

### Moving between screens

- navigate는 너가 원하는 경로로 이동해주는 것이다. 근데 이미 그 경로에 있으면 더 이상 이동 안한다. 즉, navigate를 이용해서 현재 보고 있는 화면으로 가려고 하면 아무 일도 안 일어나는 것이다. 주로 사용자가 앱 내에서 특정 위치로 가게 할 때 이 함수를 쓰면 좋다.
- 한편 push는 항상 새로운 화면을 스택에 추가한다. 이미 그 경로를 방문했다 해도, push를 호출하면 지정한 경로의 새 인스턴스가 스택에 추가되는 것이다. 사용자가 앱의 동일한 경로를 여러 번 가고 싶을 때 이 함수를 사용한다.

### Passing parameters to routes

- navigate나 push 함수의 두 번째 인자로 객체를 넘겨줄 수 있다. 이 객체는 다음 경로로 전달된다.
- 중첩된 네비게이터가 있다면, 해당 중첩된 네비게이터의 경우에는 다른 방식으로 params를 전달해주어야 한다. [link](https://reactnavigation.org/docs/params#passing-params-to-nested-navigators)

<br>

### Configuring the header bar

- Screen 컴포넌트의 options 속성을 통해서 헤더를 커스텀할 수 있다.

```js
<Stack.Screen
  name="Home"
  component={HomeScreen}
  options={{
    title: "My home",
    headerStyle: {
      backgroundColor: "#f4511e",
    },
    headerTintColor: "#fff",
    headerTitleStyle: {
      fontWeight: "bold",
    },
  }}
/>
```

- setOptions 메서드를 통해서도 헤더를 커스텀할 수 있다.
- 전체 헤더를 커스텀하고 싶다면, Stack.Navigator의 screenOptions 속성을 통해서 커스텀할 수 있다.

```js
<Stack.Navigator
      screenOptions={{
        headerStyle: {
          backgroundColor: '#f4511e',
        },
        headerTintColor: '#fff',
        headerTitleStyle: {
          fontWeight: 'bold',
        },
      }}
    >
```

- 커스텀 컴포넌트를 사용하고 싶다면, 옵션에 headerTitle을 사용하면 된다.

```js
<Stack.Navigator>
  <Stack.Screen
    name="Home"
    component={HomeScreen}
    options={{ headerTitle: props => <LogoTitle {...props} /> }}
  />
</Stack.Navigator>
```
