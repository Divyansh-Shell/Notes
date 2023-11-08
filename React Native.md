1. Graphql with the apoolo
2. Hooks 
3. Create Custom hooks 
4. Navigation 


Render Pipeline 

Fabric renderer -> fabric lets react talk to each platform and manage its host views instances they exist in js and targets interfaces of c++
react manipulates the complex host tress to respond to the external events triggered by interactions, network responses, times and so on

Renderer controls the way react intereact with host environment 

works in two modes 
Mutating modes -> create a node and set its properties and later add or remove the children from it 

Persistent Mode -> clone the parent tree and always 

React Elements 




Stability 

Regularity 

host trees -> host instances which are the nodes, host instances could be values uniquely identifying a native view from js
Every host instances have their own properties 


Render -> product logic that creates a React Element Trees in js 
Commit 
Mount 


#Sending_the_props_in_reusable_components

```
1. Make the reusable component 
2. Make an interface for the props along with the type 
	```
	interface taskProps {
    task: String;
    }
3. connect it to the reusable component 
4. Send the props from the main component using the usual flow 
5. Dont need to define the type 
```


#Network_Calling #Context #Reusable_Component 

```
1.Create the context 

	createContext();

2. Create the empty state to store the data at the time of the network calling from the api 
3. Make a function that returns the data after making the network call 
4. Return the Provider using the context 
5. Make the custom hoook using the useContext hook 
6. useContext hook -> Hook to share the state between the nested components more easily with the useState basically its the useState that can be used at the global level 
7. Wrap the custom hook around the useContext hook and make it global for use with other components
8. Wrap the entire appication using the provider for it to be available in whole app 
```


## Core Components and APIs

1.  View -> container supports flexbox, style, some touch handling and accessibilty controls 
	1. can have zero to n nested children of any type 
	2. Has all the accessibilty properties groups its children into a single selectable component 
	3.  Various props to play around with  
2. Text -> Displaying text supports nesting, styling and touch handling 
	1.  To use the consistent fonts and sizes across your application is to create a component MyAppText  that inclues them and use this component across the app

	```
	import React from 'react';
	import { Text, StyleSheet } from 'react-native';
	
	const MyAppText: React.FC<{ children: React.ReactNode }> = ({ children       }) => (
	  <Text style={styles.text}>{children}</Text>
	);
	
	const styles = StyleSheet.create({
	  text: {
	    fontSize: 16, // Adjust the font size as needed
	    fontFamily: 'YourFontFamily', // Replace with your desired font
	    // Add other text styles as needed (color, fontWeight, etc.)
	  },
	});
	
	export default MyAppText;
	
	
	
	``` 
  **This is the way to define the functional component and use it accorss   the whole project having the specific stylesheet 

```/* eslint-disable prettier/prettier */
import { Text } from "react-native";
import MyAppText from "./myapptext";
import { Component } from "react";
import React, {ReactNode} from 'react';

type MyAppHeaderTextProps = {

    children: ReactNode

}
class MyAppHeaderText extends Component<MyAppHeaderTextProps> {

    render() {

        return (

          <MyAppText>

            <Text style={{fontSize: 20, color:'red'}}>{this.props.children}</Text>

          </MyAppText>

        );

      }

    }
    export default MyAppHeaderText;
    
/*Made a wrapper class around the already defined component having the specific style which can take up the newer classes for styling the components specifically*/

Style Inheritance 

```

#Text_Input_Components 

```
import React from 'react';
import {SafeAreaView, StyleSheet, TextInput} from 'react-native';

const TextInputExample = () => {
  const [text, onChangeText] = React.useState('Useless Text');
  const [number, onChangeNumber] = React.useState('');

  return (
    <SafeAreaView>
      <TextInput
        style={styles.input}
        onChangeText={onChangeText}
        value={text}
      />
      <TextInput
        style={styles.input}
        onChangeText={onChangeNumber}
        value={number}
        placeholder="useless placeholder"
        keyboardType="numeric"
      />
    </SafeAreaView>
  );
};

const styles = StyleSheet.create({
  input: {
    height: 40,
    margin: 12,
    borderWidth: 1,
    padding: 10,
  },
});

export default TextInputExample;
```

#Multiline_Text_Input

```
import React from 'react';
import {View, TextInput} from 'react-native';

const MultilineTextInputExample = () => {
  const [value, onChangeText] = React.useState('Useless Multiline Placeholder');

  // If you type something in the text box that is a color, the background will change to that
  // color.
  return (
    <View
      style={{
        backgroundColor: value,
        borderBottomColor: '#000000',
        borderBottomWidth: 1,
      }}>
      <TextInput
        editable
        multiline
        numberOfLines={4}
        maxLength={40}
        onChangeText={text => onChangeText(text)}
        value={value}
        style={{padding: 10}}
      />
    </View>
  );
};

export default MultilineTextInputExample;
```

---
Scroll view and FlatList 

#Scroll_View  renders all its react child components at once, 

#Flatlist  renders items lazily when they are about to appear and pops out the itrems that scroll way off screen to save memory and processing time 

#Style_Sheets Methods used 
```
static flatten(style: Object[]): Object;
```

flattens the array of style objects into one aggregated style object 

Define the type of the data to be passed as an individual items having the specific properties  passed to the flatlist 

---

#Virtualization_list 

Base Implementation of the Flatlist and sectionList components, this should only be really used when there is need of more flexibilty than Flatlist provides 

Massively improves memory consumption and performance of large lists by maintaining a finite render window of active items like pagination which replaces all the items outside of the render window with appropriately sized blank spaces, content is rendered asynchronously offscreen. scrolling is faster then the fill rate and momentarily  

---
#Hooks 

useRef :  creating and accesing the refrences to components or dom elements allows to intereact with the underlying  native components directly 
	1. Accessing aand manipulating the DOM elements: Refrences the view,text and image or any other component 
	2. Soring the mutabable  values without causing re-renders: useRef can be used to store the values that should persist between the renders without causing the rerenders

---

```
import React from 'react';
import {
  StyleSheet,
  Text,
  View,
  SafeAreaView,
  SectionList,
  StatusBar,
} from 'react-native';

const DATA = [
  {
    title: 'Main dishes',
    data: ['Pizza', 'Burger', 'Risotto'],
  },
  {
    title: 'Sides',
    data: ['French Fries', 'Onion Rings', 'Fried Shrimps'],
  },
  {
    title: 'Drinks',
    data: ['Water', 'Coke', 'Beer'],
  },
  {
    title: 'Desserts',
    data: ['Cheese Cake', 'Ice Cream'],
  },
];

const App = () => (
  <SafeAreaView style={styles.container}>
    <SectionList
      sections={DATA}
      keyExtractor={(item, index) => item + index}
      renderItem={({item}) => (
        <View style={styles.item}>
          <Text style={styles.title}>{item}</Text>
        </View>
      )}
      renderSectionHeader={({section: {title}}) => (
        <Text style={styles.header}>{title}</Text>
      )}
    />
  </SafeAreaView>
);

const styles = StyleSheet.create({
  container: {
    flex: 1,
    paddingTop: StatusBar.currentHeight,
    marginHorizontal: 16,
  },
  item: {
    backgroundColor: '#f9c2ff',
    padding: 20,
    marginVertical: 8,
  },
  header: {
    fontSize: 32,
    backgroundColor: '#fff',
  },
  title: {
    fontSize: 24,
  },
});

export default App;
```

1. useRef hook is to make the reference to the native component DrawerNativeComponent to control the native methods of the drawer and it passed as ref to the component 
2. 