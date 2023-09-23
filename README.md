# CKEditor 5 editor super build generated with all features

This repository presents a CKEditor 5 editor super build with all the free plugins to use

## Quick start

1. Open the `sample/index.html` page in the browser.

## Configuring build

And use it in your website:

Or in your JavaScript application this will work with server side rendering also:

```js

import React, { useEffect, useRef, useState } from 'react';

const Ckeditor = props => {
    const editorRef = useRef();
    const [editorLoaded, setEditorLoaded] = useState(false);
    const { CKEditor, ClassicEditor } = editorRef.current || {};

    useEffect(() => {
        editorRef.current = {
            CKEditor: require('@ckeditor/ckeditor5-react').CKEditor, // v3+
            ClassicEditor: require('ckeditor-super-build/build/ckeditor'),
        };
        setEditorLoaded(true);
    }, []);


    return editorLoaded ? (
        <>
            <CKEditor
                style={{ height: '500px' }}
                editor={ClassicEditor}
                config={{
                    extraPlugins: [],
                    // ...editorConfiguration,
                }}
                // data={data}
                // disabled={isReadOnly}
                onReady={editor => {
                    // You can store the "editor" and use when it is needed.
                    editor &&
                    editor.editing &&
                    editor.editing.view &&
                    editor.editing.view.change(writer => {
                        writer.setStyle(
                            'height',
                            height,
                            editor.editing.view.document.getRoot(),
                        );
                    });

                    editor && editor.ui && editor.ui.getEditableElement().parentElement.insertBefore(
                        editor.ui.view.toolbar.element,
                        editor.ui.getEditableElement()
                    );
                    onReady(editor);
                }}
                onChange={(event, editor) => {
                    const data = editor.getData();
                    // onchange(event, editor, data);
                }}
                onBlur={(event, editor) => {
                    onBlur('Blur.', editor);
                }}
                onFocus={(event, editor) => {
                    onFocus('Focus.', editor);
                }}
            />
        </>
    ) : (
        <div>Editor loading</div>
    );
};

export default Ckeditor;

```

**Note:** If you are planning to integrate CKEditor&nbsp;5 deep into your application, it is actually more convenient and recommended to install and import the source modules directly (like it happens in `ckeditor.js`). Read more in the [Advanced setup guide](https://ckeditor.com/docs/ckeditor5/latest/installation/advanced/alternative-setups/integrating-from-source-webpack.html).

## License

Licensed under the terms of [GNU General Public License Version 2 or later](http://www.gnu.org/licenses/gpl.html). For full details about the license, please check the `LICENSE.md` file or [https://ckeditor.com/legal/ckeditor-oss-license](https://ckeditor.com/legal/ckeditor-oss-license).

### Installation

In order to rebuild the application you need to install all dependencies first. To do it, open the terminal in the project directory and type:

```
npm install
```

Make sure that you have the `node` and `npm` installed first. If not, then follow the instructions on the [Node.js documentation page](https://nodejs.org/en/).

### Adding or removing plugins

Now you can install additional plugin in the build. Just follow the [Adding a plugin to an editor tutorial](https://ckeditor.com/docs/ckeditor5/latest/builds/guides/integration/installing-plugins.html#adding-a-plugin-to-an-editor)

### Rebuilding editor

If you have already done the [Installation](#installation) and [Adding or removing plugins](#adding-or-removing-plugins) steps, you're ready to rebuild the editor by running the following command:

```
npm run build
```

This will build the CKEditor 5 to the `build` directory. You can open your browser and you should be able to see the changes you've made in the code. If not, then try to refresh also the browser cache by typing `Ctrl + R` or `Cmd + R` depending on your system.

## What's next?

Follow the guides available on https://ckeditor.com/docs/ckeditor5/latest/framework/index.html and enjoy the document editing.

## FAQ
| Where is the place to report bugs and feature requests?

You can create an issue on https://github.com/ckeditor/ckeditor5/issues. Make sure that the question / problem is unique, please look for a possibly asked questions in the search box. Duplicates will be closed.

| Where can I learn more about the CKEditor 5 framework?

Here: https://ckeditor.com/docs/ckeditor5/latest/framework/

| Is it possible to use online builder with common frameworks like React, Vue or Angular?

Not yet, but it these integrations will be available at some point in the future.
