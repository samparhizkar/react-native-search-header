# react-native-seach-header
Easy to use React Native search header component based on material design patterns.
This react native component was built with [hyperflow](http://github.com/tuantle/hyperflow) (a state management and mutation tool).

![demo](/demo.gif)

## Installation

`$ npm install react-native-search-header --save`

## Usage

To use search header you simply import the component factory function to create a renderable component:

```js
import SearchHeaderComponent from 'react-native-search-header';

const SearchHeaderView = SearchHeaderComponent();
```

### Examples

To use search header you simply import the component factory function to create a renderable component:

```js
import React, { Component } from 'react';
import {
    Dimensions,
    AppRegistry,
    StyleSheet,
    View,
    Text,
    Button,
    StatusBar
} from 'react-native';

import SearchHeaderComponent from 'react-native-search-header';

const DEVICE_WIDTH = Dimensions.get(`window`).width;

const SearchHeader = SearchHeaderComponent();

const styles = StyleSheet.create({
    container: {
        flex: 1,
        justifyContent: 'flex-start',
        alignItems: 'center',
        backgroundColor: '#f5fcff'
    },
    status: {
        zIndex: 10,
        elevation: 2,
        width: DEVICE_WIDTH,
        height: 21,
        backgroundColor: '#0097a7'
    },
    header: {
        justifyContent: 'center',
        alignItems: 'center',
        width: DEVICE_WIDTH,
        height: 56,
        marginBottom: 6,
        backgroundColor: '#00bcd4'
    },
    label: {
        flexGrow: 1,
        fontSize: 20,
        fontWeight: `600`,
        textAlign: `left`,
        marginVertical: 8,
        paddingVertical: 3,
        color: `#f5fcff`,
        backgroundColor: `transparent`
    },
    button: {
        justifyContent: 'center',
        alignItems: 'center',
        width: 130,
        height: 40,
        marginTop: 40,
        borderRadius: 2,
        backgroundColor: `#ff5722`
    }
});

export default class Demo extends Component {
    constructor (
        props : Object,
        context : Object
    ) {
        super(props, context);
    }
    render () {
        return (
            <View style = { styles.container }>
                <StatusBar barStyle = 'light-content' />
                <View style = { styles.status }/>
                <View style = { styles.header }>
                    <Text style = { styles.label }>Demo</Text>
                </View>
                <SearchHeader
                    ref = {(searchHeader) => {
                        this.searchHeader = searchHeader;
                    }}
                    statusHeightOffet = { 21 }
                />
                <View style = { styles.button }>
                    <Button
                        title = 'Open Search'
                        color = '#f5fcff'
                        onPress = {() => this.searchHeader.doShowSearch()}
                    />
                </View>
            </View>
        );
    }
}

AppRegistry.registerComponent('Demo', () => Demo);
```

## Public Methods Access via Reference

    These are methods that are accessible via "ref":

Methods | description
-----|------
doShowSearch | Call to show the SearchHeader.
doHideSearch | Call to hide the SearchHeader.
doClearSearchSuggestion | Call to clear search suggestion list.

## Props

Below are the props you can pass to the React Component to customize the SearchHeader.

Prop | Type | Default | description
-----|------|---------|------------
searchTextColor | string | #5d5d5d | Search text input color.
placeholderTextColor | string | #bdbdbd | Text input placeholder color.
iconColor | string | #5d5d5d | SearchHeader component icon button color.
statusHeightOffet | number | 21 | The offset above the SearchHeader component. Usually where the phone status is.
dropShadow | boolean | true | Enable drop shadow styling.
searchVisibleInitially | boolean | false | Set to false to hide and to true to show the SearchHeader component.
autoCorrect | boolean | true | Enable text input autocorrect.
enableSearchSuggestion | boolean | true | When enabled, search suggestion list will be display accordingly.
searchSuggestionRollOverCount | number | 16 | The max number of search suggestion items.
placeholder | string | "Search..." | A string placeholder when there is no text in text input.
onGetSearchSuggestions | function | None | This function is called during search change (componenWillUpdate) to get a string array of search suggestions.
onSearch | function | None | This function is called after return/done key is pressed. Return text input event.
onSearchChange | function | None | This function is called after text is entered/changed in text input. Return text input event.
onSearchFocus | function | None | This function is called when text input in focused.
onSearchBlur | function | None | This function is called when text input in blurred.
onSearchHidden | function | None | This function is called right after hide animation is completed.
onSearchVisible | function | None | This function is called right after show animation is completed.

### Style Overrides

SearchHeader component default style can be override. Below are examples of how to override each default style element.

```js
<SearchHeader
	style = {{
		container: {
			...myContainerStyle
		},
		search: {
			...mySearchStyle
		},
		searchSuggestion: {
			...mySearchSuggestionStyle
		},
		searchText: {
			...mySearchTextStyle
		},
		searchSuggestionItemText: {
			...mySearchSuggestionItemTextStyle
		},
		icon: {
			...myIconStyle
		}
	}}
/>
```

## Change Log

**Release Version 0.1.0 (01/22/2017)**
```
Notes:
    - Initial commit with features
	    Search header component based on material design.
	    Search suggestions and history with autocomplete. patterns
New Features:
Breaking Changes:
Improvements:
Bug fixes:
```
**Release Version 0.1.1 (01/23/2017)**
```
Notes:
	- Update to latest hyperflow version.
New Features:
Breaking Changes:
Improvements:
Bug fixes:
```
**Release Version 0.1.2 (01/23/2017)**
```
Notes:
	- Update to latest hyperflow version.
New Features:
Breaking Changes:
    - Props renaming:
        statusBarHeightOffet      -> statusHeightOffet
        textInputPlaceholderColor -> placeholderTextColor
        minimized                 -> searchVisibleInitially
        onBlur                    -> onSearchBlur
        onFocus                   -> onSearchFocus
        onMinimized               -> onSearchHidden
        onMaximized               -> onSearchVisible
Improvements:
    - Added public methods access via "ref"
Bug fixes:
```

## TODO

-   Fix flashing animation issue.
-   Fix react "refs" warning message.

## License

Hyperflow is [MIT licensed](./LICENSE).
