# React Native Camera Rool Picker (remobile)
A React Native component providing images selection from camera roll.

## Installation
```sh
npm install @remobile/react-native-camera-roll-picker --save
```

## Usage

### Example
```js
var React = require('react');
var ReactNative = require('react-native');
var {
    StyleSheet,
    Text,
    View,
} = ReactNative;

var CameraRollPicker = require('@remobile/react-native-camera-roll-picker');

module.exports = React.createClass({
    getInitialState() {
        return {
            num: 0,
            selected: [],
        };
    },
    onSelectedImages(images, current) {
        var num = images.length;

        this.setState({
            num: num,
            selected: images,
        });

        console.log(current);
        console.log(this.state.selected);
    },
    openCamera() {
        console.log("open camera here");
    },
    render() {
        return (
            <View style={styles.container}>
                <View style={styles.content}>
                    <Text style={styles.text}>
                        <Text style={styles.bold}>
                            {this.state.num}
                        </Text>
                        images has been selected
                    </Text>
                </View>
                <CameraRollPicker
                    scrollRenderAheadDistance={500}
                    initialListSize={1}
                    pageSize={3}
                    removeClippedSubviews={false}
                    groupTypes='SavedPhotos'
                    batchSize={5}
                    maximum={1}
                    selected={this.state.selected}
                    assetType='Photos'
                    imagesPerRow={3}
                    imageMargin={5}
                    onSelectedImages={this.onSelectedImages}
                    openCamera={this.openCamera} />
            </View>
        );
    },
});

const styles = StyleSheet.create({
    container: {
        flex: 1,
        backgroundColor: '#F6AE2D',
    },
    content: {
        marginTop: 15,
        height: 50,
        flexDirection: 'row',
        justifyContent: 'center',
        alignItems: 'center',
        flexWrap: 'wrap',
    },
    text: {
        fontSize: 16,
        alignItems: 'center',
        color: '#fff',
    },
    bold: {
        fontWeight: 'bold',
    },
    info: {
        fontSize: 12,
    },
});
```

## Screencasts

![demo](https://github.com/remobile/react-native-camera-roll-picker/blob/master/screencasts/demo.png)

#### Props
- `onSelectedImages` : Callback function when images was selected. (is required!). Return a selected image array and current selected image.
- `openCamera` : Open camera function.
- `scrollRenderAheadDistance` : "How early to start rendering rows before they come on screen, in pixels." (Default: 500)
- `initialListSize` : Specifies how many rows we want to render on our first render pass. (Default: 1)
- `pageSize` : After the initial render where 'initialListSize' is used, ListView looks at the pageSize to determine how many rows to render per frame. (Default: 3)
- `removeClippedSubViews` : "When true, offscreen child views (whose overflow value is hidden) are removed from their native backing superview when offscreen. This can improve scrolling performance on long lists. The default value is true." (The default value is false before version 0.14-rc). (Default: true)
- `groupTypes` : The group where the photos will be fetched, one of 'Album', 'All', 'Event', 'Faces', 'Library', 'PhotoStream' and 'SavedPhotos'. (Default: SavedPhotos)
- `assetType` : The asset type, one of 'Photos', 'Videos' or 'All'. (Default: Photos)
- `selected` : Already be selected images array. (Default: [])
- `maximum` : Maximum number of selected images. (Default: 15)
- `imagesPerRow` : Number of images per row. (Default: 3)
- `imageMargin` : Margin size of one image. (Default: 5)
- `containerWidth` : Width of camer roll picker container. (Default: device width)
- `selectedMarker` : Custom selected image marker component. (Default: checkmark).
- `backgroundColor` : Set background color. (Default: white).
- `emptyText`: Text to display instead of a list when there are no photos found. (Default: 'No photos.')
- `emptyTextStyle`: Styles to apply to the `emptyText`. (Default: `textAlign: 'center'`)

### thanks
* this project code come from https://github.com/jeanpan/react-native-camera-roll-picker
