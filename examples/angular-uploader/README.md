# Blocks ❤️ Angular

<!-- [![Edit angular-uploader](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/github/uploadcare/blocks-examples/tree/main/examples/angular-uploader/) -->

## Integration notes

### Set NgModule schema

Since Blocks are based on custom elements, you need to let Angular know that you are using them.
This is done by setting `@NgModule`'s `schema` property to `CUSTOM_ELEMENTS_SCHEMA`:

```typescript
import { NgModule, CUSTOM_ELEMENTS_SCHEMA } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule],
  providers: [],
  bootstrap: [AppComponent],
  schemas: [CUSTOM_ELEMENTS_SCHEMA],
})
export class AppModule {}
```

See [Angular docs](https://angular.io/api/core/NgModule#schemas) for more information.

### Disable emulated view encapsulation

Angular's emulated view encapsulattion don't support custom elements, it brakes our styles.
To disable it, set `@Component`'s `encapsulation` property to `ViewEncapsulation.ShadowDom` or `ViewEncapsulation.None`:

```typescript
import { Component, ViewEncapsulation } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css'],
  encapsulation: ViewEncapsulation.ShadowDom // or ViewEncapsulation.None
})
export class AppComponent {}
```

See [Angular docs](https://angular.io/guide/view-encapsulation#view-encapsulation) for more information.
