# ckeditor-loader
webpack loader to load ckeditor


## USAGE

code:
```javascript
import $ from 'jquery';
import React, {Component} from 'react';
import ReactDOM from 'react-dom';

import Editor from './ckeditor.conf';

window.$ = $;
window.editor = Editor;

class App extends Component {

  componentDidMount() {
    var context = this.refs.editorContext;
    this.editor = Editor.appendTo(context, {
      customConfig: '',
      width: 640,
      height: 480,
    });
  }

  render() {
    return (
      <div className="wrapper">
        <header>
          <h1>CKEditor</h1>
        </header>
        <section>
          <div ref="editorContext" />
        </section>
      </div>
    );
  }
}

$(function() {
  ReactDOM.render(
    <App />,
    document.getElementById('app'),
    () => {
      console.log('App mounted!');
    }
  );
});


```

editor.conf:
```javascript
{
    "plugins": ["link", "table"],
    "languages": ["zh", "en"],
    "theme": "moono"
};
```

loader:
```javascript
module: {
    rules: [
    ...
    {
        test: /ckeditor.conf$/,
        use: [
            'ckeditor-loader'
        ]
    }
    ]
```
