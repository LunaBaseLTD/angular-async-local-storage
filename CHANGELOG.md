# Changelog

## 6.0.0-rc.0 (2018-05-03)

Note: we are confident with this release to be used with Angular 6 final.
But as we may switch to the new official CLI library generation,
we're staying in Release Candidate until then to avoid any unexpected breaking change.

### Features

- Support of Angular 6, install with: `npm install @ngx-pwa/local-storage@latest`

- New JSON Schema validation options supported (see [#18](https://github.com/cyrilletuzi/angular-async-local-storage/issues/18) for the full list).

- `setItemSubscribe()`, `removeItemSubscribe()`, `clearSubscribe()` methods for auto-subscription

- `localStorageProviders({ prefix: 'myapp' })` to avoid collision in multiple apps on same subdomain 

- Tree-shakable providers.

- `sideEffects: false` for webpack optimization
- Partial support of official [Angular Package Format v6](https://docs.google.com/document/d/1CZC2rcpxffTDfRDs6p1cfbmKNLA6x5O-NtkJglDaBVs/edit)
(non-flatenned packages are not yet available, waiting for more info on this)

### Breaking changes

#### New requirements
  - Angular 6
  - TypeScript 2.7
  - RxJS 6

#### New names

- This lib has been renamed to `@ngx-pwa/local-storage`. See the [migration guide](https://github.com/cyrilletuzi/angular-async-local-storage/blob/master/MIGRATION.md).

- Classes renamed. See the [migration guide](https://github.com/cyrilletuzi/angular-async-local-storage/blob/master/MIGRATION.md).
  - `AsyncLocalStorage` removed, renamed to `LocalStorage`.
  - `AsyncLocalDatabase` removed, renamed to `LocalDatabase`.
  - `ALSGetItemOptions` removed, renamed to `LSGetItemOptions`.

#### Validation

- To be consistent with the strict validation, and to prepare future enhancement of JSON Schema typings,
it is no longer possible to specify an array for `type`.
- `JSONSchemaType` has been removed. It should very unlikely concern you, it was an internal type.

#### Others

- `LocalStorageModule` no longer needed and so removed. Just delete the import in your `AppModule`.

- Distribution files and directories of non-UMD packages have been changed to match
official [Angular Package Format v6](https://docs.google.com/document/d/1CZC2rcpxffTDfRDs6p1cfbmKNLA6x5O-NtkJglDaBVs/edit).
It should not affect your code, as building tools like webpack know where to find the new packages.

## 5.3.0 (2018-05-03)

### Feature

- `localStorageProviders({ prefix: 'myapp' })` to avoid collision in multiple apps on same subdomain

## 5.2.0 (2018-04-08)

### Feature

- `setItemSubscribe()`, `removeItemSubscribe()`, `clearSubscribe()` methods for auto-subscription

## 5.1.1 (2018-04-07)

### Bug fix

- Correct too wide type inference for `getItem()`

## 5.1.0 and 4.1.0 (2018-04-07)

### Refactoring

- `AsyncLocalStorageModule` deprecated (but still working). Renamed to `LocalStorageModule`
- `AsyncLocalStorage` deprecated (but still working). Renamed to `LocalStorage`
- `AsyncLocalDatabase` deprecated (but still working). Renamed to `LocalDatabase`
- `ALSGetItemOptions` deprecated (but still working). Renamed to `LSGetItemOptions`

See the [migration guide](https://github.com/cyrilletuzi/angular-async-local-storage/blob/master/MIGRATION.md).

## 5.0.0 (2018-04-03)

### New package name

This lib has been renamed from `angular-async-local-storage` to `@ngx-pwa/local-storage`. See the [migration guide](https://github.com/cyrilletuzi/angular-async-local-storage/blob/master/MIGRATION.md).

### Version alignement

This lib major version is now aligned to the major version of Angular. Meaning this v5 is for Angular 5. Same as v3.1.4.

## 4.0.0 (lts) (2018-04-03)

### New package name

This lib has been renamed from `angular-async-local-storage` to `@ngx-pwa/local-storage`. See the [migration guide](https://github.com/cyrilletuzi/angular-async-local-storage/blob/master/MIGRATION.md).

### Version alignement

This lib major version is now aligned to the major version of Angular. Meaning this v4 is for Angular 4. Same as v2.

We follow [Angular LTS support](https://github.com/angular/angular/blob/master/docs/RELEASE_SCHEDULE.md),
meaning we support Angular 4 until October 2018. So we backported some bug fixes:

- Detect if storages are null or undefined (partially fixes (partially fixes [#26](https://github.com/cyrilletuzi/angular-async-local-storage/issues/26))
- Correctly complete observables (fixes [#25](https://github.com/cyrilletuzi/angular-async-local-storage/issues/25) & [#5](https://github.com/cyrilletuzi/angular-async-local-storage/issues/5))
- Some IndexedDB connection errors were not caught

***

Previous versions were only released under `angular-async-local-storage`.

***

## 3.1.4 (2018-03-24)

### Bug fix

- Detect if storages are null (partially fixes [#26](https://github.com/cyrilletuzi/angular-async-local-storage/issues/26))

## 3.1.3 (2018-03-23)

### Bug fix

- Detect if storages are undefined (partially fixes [#26](https://github.com/cyrilletuzi/angular-async-local-storage/issues/26))

## 3.1.2 (2018-03-23)

### Bug fix

- Correctly complete observables (fixes [#25](https://github.com/cyrilletuzi/angular-async-local-storage/issues/25) & [#5](https://github.com/cyrilletuzi/angular-async-local-storage/issues/5))

## 3.1.1 (2018-01-04)

### Bug fixes

- Some IndexedDB connection errors were not caught
- Browser info has been added for IndexedDB errors

## 3.1.0 (2017-11-29)

### Features

- JSON Schema validation
- Extensibility : add your own storage

See README for instructions.

## 3.0.0 (2017-11-03)

### Breaking changes

- Angular 5 is now supported and required
- RxJS >= 5.5.2 is now supported and required : [lettable operators](https://github.com/ReactiveX/rxjs/blob/master/doc/lettable-operators.md)

## 2.0.1 (2017-10-03)

### Bug fix

- RxJS operators can now be used again on returned observables (fixes [#10](https://github.com/cyrilletuzi/angular-async-local-storage/issues/10))

## 2.0.0 (2017-09-16)

### Features

- Implements [Angular Package Format](https://docs.google.com/document/d/1CZC2rcpxffTDfRDs6p1cfbmKNLA6x5O-NtkJglDaBVs/)
  - Compatible with Universal builds from Angular CLI >= 1.3 (fixes [#9](https://github.com/cyrilletuzi/angular-async-local-storage/issues/9))
  - Compatible with ES2015+ target builds (= smaller builds)
- Better type checking with generics : `this.storage.getItem<string>('color')`

### Breaking changes

- Angular 4 is now required
- TypeScript >= 2.3 is now required

### Under the hood

- Use Angular 4 platform tests to detect storages support instead of try/catch
- Unit tests

## 1.4.0 (2017-04-01)

### Features

- Up to date with Angular 4.0

## 1.3.0 (2016-12-27)

### Features

- Rename package to angular-async-local-storage

***

Previous versions were only released under `angular2-async-local-storage`.

***

## 1.2.0 (2016-12-20)

### Features

- Up to date with Angular 2.4 and RxJS final

## 1.1.1 (2016-12-19)

### Bug fixes

- Recompiled with Angular 2.3.1, following [Angular changelog advice](https://github.com/angular/angular/blob/master/CHANGELOG.md#231-2016-12-15)

## 1.1.0 (2016-12-09)

### Features

- Up to date with Angular 2.3
- Update peerDependencies :
  - reflect-metadata 0.1.8
  - rxjs 5.0.0-rc.4
  - zone.js 0.7.2

## 1.0.2 (2016-11-01)

### Bug fixes

- allow falsy values in mock database

## 1.0.1 (2016-11-01)

### Bug fixes

- null instead of undefined for unexisting item in mock database

## 1.0.0 (2016-10-31)

### Features

- Initial release : asynchronous local storage module for Angular
- Up to date with Angular 2.1
- Compatible with AoT pre-compiling
- Compatible with Universal server-side rendering
- IE9 support via native localStorage (public API still asynchronous but synchronous internally)
