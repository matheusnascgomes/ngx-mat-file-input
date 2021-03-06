[![Build Status](https://travis-ci.org/merlosy/ngx-material-file-input.svg?branch=master)](https://travis-ci.org/merlosy/ngx-material-file-input)
[![npm](https://img.shields.io/npm/dt/ngx-material-file-input.svg)](https://www.npmjs.com/package/ngx-material-file-input)
[![](http://img.badgesize.io/https://unpkg.com/ngx-material-file-input@latest/bundles/ngx-material-file-input.umd.min.js?label=full%20size%20as%20min.js&compression=gzip&style=square&color=02adff)](https://www.npmjs.com/package/ngx-material-file-input)
[![Coverage Status](https://coveralls.io/repos/github/merlosy/ngx-material-file-input/badge.svg)](https://coveralls.io/github/merlosy/ngx-material-file-input)
[![Known Vulnerabilities](https://snyk.io/test/github/merlosy/ngx-material-file-input/badge.svg)](https://snyk.io/test/github/merlosy/ngx-material-file-input)

# mat-file-input

### :warning: This project is a fork of the [ngx-material-file-input](https://github.com/merlosy/ngx-material-file-input)

This project provides:

- `ngx-mat-file-input` component, to use inside Angular Material `mat-form-field`
- a `FileValidator` with `maxContentSize`, to limit the file size
- a `ByteFormatPipe` to format the file size in a human-readable format

For more code samples, have a look at the [DEMO SITE](https://merlosy.github.io/ngx-material-file-input)

## Install

```bash
npm i ngx-mat-file-input
```

Or using Yarn

```bash
yarn add ngx-mat-file-input
```

## Usage

First, import the `MaterialFileInputModule` into your feature module (or app.module):

```ts
import { MaterialFileInputModule } from 'ngx-mat-file-input';

@NgModule({
  imports: [
    // the module for this lib
    MaterialFileInputModule
  ]
})
```

Now you can use the `<ngx-mat-file-input>` element:

```html
<mat-form-field appearance="outline">
  <ngx-mat-file-input
    id="my-id"
    valuePlaceholder="doc.placeholder"
    (change)="uploadDocument($event)"
    [multiple]="true"
    [disabled]="false"
  ></ngx-mat-file-input>
  <small
    >Allowed formats: .pdf, .png, .jpg, .jpeg, .docx. <br />
    Max file size. {{ maxFileSize | byteFormat }}</small
  >
</mat-form-field>
```

## API reference

### `MaterialFileInputModule`

```ts
import { MaterialFileInputModule } from 'ngx-mat-file-input';

@NgModule({
  imports: [
    // the module for this lib
    MaterialFileInputModule
  ]
})
```

#### `NGX_MAT_FILE_INPUT_CONFIG` token (optional):

Change the unit of the ByteFormat pipe

```ts
export const config: FileInputConfig = {
  sizeUnit: 'Octet',
};

// add with module injection
providers: [{ provide: NGX_MAT_FILE_INPUT_CONFIG, useValue: config }];
```

### `FileInputComponent`

selector: `<ngx-mat-file-input>`

implements: [MatFormFieldControl](https://material.angular.io/components/form-field/api#MatFormFieldControl)<FileInput> from Angular Material

**Additionnal properties**

| Name                                  | Description                                                                                                                 |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| _@Input()_ valuePlaceholder: `string` | Placeholder for file names, empty by default                                                                                |
| _@Input()_ multiple: `boolean`        | Allows multiple file inputs, `false` by default                                                                             |
| _@Input()_ autofilled: `boolean`      | Whether the input is currently in an autofilled state. If property is not present on the control it is assumed to be false. |
| _@Input()_ accept: `string`           | Any value that `accept` attribute can get. [more about "accept"](https://www.w3schools.com/tags/att_input_accept.asp)       |
| value: `FileInput`                    | Form control value                                                                                                          |
| empty: `boolean`                      | Whether the input is empty (no files) or not                                                                                |
| clear(): `(event?) => void`           | Removes all files from the input                                                                                            |

### `ByteFormatPipe`

**Example**

```html
<span>{{ 104857600 | byteFormat }}</span>
```

_Output:_ 100 MB

### `FileValidator`

| Name                                                     | Description                                                                                                    | Error structure                              |
| -------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| maxContentSize(value: `number`): `ValidatorFn`           | Limit the total file(s) size to the given value                                                                | `{ actualSize: number, maxSize: number }`    |
| allowedExtensions(extentions: `string[]`): `ValidatorFn` | Handles allowed file types by controlling whether some specific extensions matches with the uploaded file type | `{ allowedExtentions: allowedExtentions[] }` |

## License

MIT.

Special thanks to [Merlosy](https://github.com/merlosy) to created this lib.

&star; to show support :)
