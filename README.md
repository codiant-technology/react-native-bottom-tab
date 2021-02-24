# React native animated bottom tab

### Getting Started

### Installation

```sh
npm i react-native-bottom-tab react-native-svg
```

### Usage

> It provides a animated bottom tab component as shown in image and can be best use with createBottomTabNavigator from react-navigation.

<img src="https://github.com/codiant-technology/react-native-bottom-tab/blob/main/demo.gif" style="align-self: center;height: 500, width: 400" />

### Example

```js
import React from "react";
import { SafeAreaView, Text } from "react-native";
import { createBottomTabNavigator } from "@react-navigation/bottom-tabs";
import Images from "../../common/Images";
import TabBar, { EventRegister } from "react-native-bottom-tab";

const TabBarDemo = [
  {
    name: "Home",
    icon: Images.ic_bottom_tab_home,
  },
  {
    name: "Profile",
    icon: Images.ic_bottom_tab_me,
  },
  {
    name: "Settings",
    icon: Images.ic_setting,
  },
  {
    name: "Todo",
    icon: {
      uri:
        "https://cdn.iconscout.com/icon/premium/png-512-thumb/todo-2938970-2429411.png",
    },
  },
  {
    name: "Lists",
    icon: {
      uri: "https://cdn3.iconfinder.com/data/icons/document-42/32/2-512.png",
    },
  },
];

const Home = () => {
  return (
    <SafeAreaView>
      <Text>{`Home`}</Text>
    </SafeAreaView>
  );
};

const Profile = ({ navigation }) => {
  return (
    <SafeAreaView>
      <Text
        onPress={() => {
          navigation.navigate("Home");
          EventRegister.emit("setBottomBarIndex", 1);
        }}
      >{`Home`}</Text>
      <Text
        onPress={() => {
          navigation.navigate("Settings");
          EventRegister.emit("setBottomBarIndex", 3);
        }}
      >{`Settings`}</Text>
      <Text
        onPress={() => {
          navigation.navigate("Todo");
          EventRegister.emit("setBottomBarIndex", 4);
        }}
      >{`Todo`}</Text>
      <Text
        onPress={() => {
          navigation.navigate("Lists");
          EventRegister.emit("setBottomBarIndex", 5);
        }}
      >{`Lists`}</Text>
    </SafeAreaView>
  );
};

const Settings = () => {
  return (
    <SafeAreaView>
      <Text>{`Settings`}</Text>
    </SafeAreaView>
  );
};

const Todo = ({ navigation }) => {
  return (
    <SafeAreaView>
      <Text>{`Todo`}</Text>
    </SafeAreaView>
  );
};

const Lists = () => {
  return (
    <SafeAreaView>
      <Text>{`Lists`}</Text>
    </SafeAreaView>
  );
};

const Tab = createBottomTabNavigator();

const TabBarDemo = ({ navigation }) => {
  const navigateTo = (routeName = "Profile") => {};

  return (
    <Tab.Navigator
      tabBar={(props) => (
        <TabBar
          tabBackgroundColor="#000000"
          iconTintColor="#fff"
          activeIconTintColor="#fafafa"
          activeBackgroundColor="#3d0b0b"
          tabs={TabBarDemo}
          {...props}
        />
      )}
    >
      <Tab.Screen name="Home" component={Home} />
      <Tab.Screen name="Profile" component={Profile} />
      <Tab.Screen name="Settings" component={Settings} />
      <Tab.Screen name="Todo" component={Todo} />
      <Tab.Screen name="Lists" component={Lists} />
    </Tab.Navigator>
  );
};

export default TabBarDemo;
```

| Prop                      | Description                      | Default     |
| ------------------------- | -------------------------------- | ----------- |
| _`tabs`_                  | Tabs to render                   | defaultTabs |
| _`tabBackgroundColor`_    | background color of tab bar      | #000        |
| _`iconTintColor`_         | Tint color of icon               | #fff        |
| _`activeIconTintColor`_   | Tint color of active icon        | #fafafa     |
| _`activeBackgroundColor`_ | Backgropund color of active icon | #3d0b0b     |
