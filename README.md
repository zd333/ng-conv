# :kiss: Set of conventions/guides/best practices for NGRX Angular apps

**Default NGRX, Angular, TypeScript style guides, best practices and conventions/patterns are must (with corresponding priority) unless there is specific convention in this doc.**

[:sob: Folder structure](#folder-structure)

[:skull: Types](#types)

[:trollface: Naming](#naming)

[:sos: State](#state)

[:see_no_evil: Components](#components)

[:underage: Services](#services)

[:rainbow: Routing](#routing)

[:circus_tent: Misc](#misc)

## Folder structure

* keep folder structure as flat as possible, try to add domains (features) as siblings even if they seem to be logically nested (avoid domain1->sub_domain1_1->sub_domain1_1_1 folder nesting)
* do not replicate routing structure in project folder structure, they can have different hierarchy; project folder structure should be convenient for developers, routing (paths) structure should be convenient for end-user
* do not nest component folders (use flat structure with sibling folders), even for sub-components
* do not use a dedicated folder for shared services, just provide them in `feature-shared.module.ts` (via providedIn)
* keep everything that describes data structures (all interfaces, types and classes, but not enums) in `types` folders
* keep enums in `constants` folder
* place types (interfaces, classes), constants, enumns into a dedicated file (in `types`/`constants` folder) only if it is exported and used in multiple files/places

```bash
├── app-component.ts
├── app-module.ts
├── app-core.module.ts
├── app-routing.module.ts
├── app-shared.module.ts
├── +state
│   ├── app-state.module.ts
│   ├── selectors
│   │   ├── index.ts
│   │   ├── some-auth.selector.ts
│   │   ├── another-auth.selector.ts
│   │   ├── some-root.selector.ts
│   │   ├── another-root.selector.ts
│   │   ├── route-url.selector.ts
│   │   ├── route-param.selector.ts
│   │   ├── route-query-param.selector.ts
│   │   └── some-compound.selector.ts
│   └── slices
│       ├── auth
│       │   ├── auth.actions.ts
│       │   ├── auth.effects.ts
│       │   ├── auth.reducer.ts
│       │   └── auth-state.facade.ts
│       ├── router
│       │   ├── route-serializer.ts
│       │   └── router-state.facade.ts
│       └── root
│           ├── root.actions.ts
│           ├── root.effects.ts
│           ├── root.reducer.ts
│           └── root-state.facade.ts
├── components
│   ├── index.ts
│   ├── some-common-dumb
│   │   ├── some-common-dumb-component.module.ts
│   │   ├── some-common-dumb.component.html
│   │   ├── some-common-dumb.component.scss
│   │   └── some-common-dumb.component.ts
│   ├── some-specific-dumb
│   │   ├── some-specific-dumb.component.html
│   │   ├── some-specific-dumb.component.scss
│   │   └── some-specific-dumb.component.ts
│   ├── some-container
│   │   ├── some-container.component.html
│   └── └── some-container.component.ts
├── constants
│   ├── index.ts
│   ├── auth-initial-state.constant.ts
│   ├── root-initial-state.constant.ts
│   ├── app-routing-param-names.constant.ts
│   ├── error-codes.enum.ts
│   └── some-shared-constant.constant.ts
├── guards
│   ├── index.ts
│   └── some.guard.ts
├── helpers
│   ├── index.ts
│   └── some-helping-function.ts
├── services
│   ├── index.ts
│   ├── auth-api-connector.service.ts
│   ├── some-business-logic.service.ts
│   └── some-entity-api-connector.service.ts
└── types
│   ├── index.ts
│   ├── auth-state.interface.ts
│   ├── login-response.interface.ts
│   ├── root-state.interface.ts
│   └── whatever-data-struct.type.ts
└── domains
    ├── some-feature1
    │   ├── some-feature1.module.ts
    │   ├── some-feature1-core.module.ts
    │   ├── some-feature1-routing.module.ts
    │   ├── some-feature1-shared.module.ts
    │   ├── +state
    │   │   ├── some-feature1-state.module.ts
    │   │   ├── entity-x.actions.ts
    │   │   ├── entity-x.effects.ts
    │   │   ├── entity-x.reducer.ts
    │   │   ├── entity-x-state.facade.ts
    │   │   └── selectors
    │   │       ├── index.ts    
    │   │       ├── some-entity-x.selector.ts
    │   │       └── another-entity-x.selector.ts    
    │   ├── components
    │   │   ├── index.ts
    │   │   ├── another-common-dumb
    │   │   │   ├── another-common-dumb-component.module.ts    
    │   │   │   ├── another-common-dumb.component.html
    │   │   │   ├── another-common-dumb.component.scss
    │   │   │   └── another-common-dumb.component.ts
    │   │   └── another-container
    │   │       ├── another-container.component.html
    │   │       └── another-container.component.ts
    │   ├── constants
    │   │   ├── index.ts
    │   │   ├── some-feature1-routing-param-names.constant.ts    
    │   │   └── entity-x-initial-state.constant.ts
    │   ├── guards
    │   │   ├── index.ts
    │   │   └── another.guard.ts
    │   ├── services
    │   │   ├── index.ts
    │   │   └── entity-x-api-connector.service.ts
    │   └── types
    │       ├── index.ts
    │       └── entity-x-state.interface.ts
    └── some-feature2
        ├── some-feature2.module.ts    
        ├── some-feature2-core.module.ts
        ├── +state
        │   ├── some-feature2-state.module.ts        
        │   ├── selectors
        │   │   ├── index.ts        
        │   │   ├── some-entity-y.selector.ts
        │   │   └── some-entity-z.selector.ts
        │   └── slices
        │       ├── entity-y
        │       │   ├── entity-y.actions.ts        
        │       │   ├── entity-y.effects.ts
        │       │   ├── entity-y.reducer.ts
        │       │   └── entity-y-state.facade.ts
        │       └── entity-z     
        │           ├── entity-z.actions.ts
        │           ├── entity-z.effects.ts
        │           ├── entity-z.reducer.ts
        │           └── entity-z-state.facade.ts
        ├── components
        │   ├── index.ts
        │   └── yet-another-container
        │       ├── yet-another-container.component.html
        │       └── yet-another-container.component.ts
        ├── constants
        │   ├── index.ts        
        │   ├── entity-y-initial-state.constant.ts
        │   └── entity-z-initial-state.constant.ts
        ├── services
        │   ├── index.ts
        │   ├── entity-y-api-connector.service.ts        
        │   └── entity-z-api-connector.service.ts
        └── types
            ├── index.ts        
            ├── entity-y-state.interface.ts
            └── entity-z-state.interface.ts
```

## Types

* avoid `null` values
* avoid classes (except library ones), always prefer interfaces/types
* avoid ubiquitous direct usage of types from external libs (including API DTOs/DAOs), only use those types in the code units that directly work with the lib (e.g. API connector service can directly use DTO interface from API lib), for other cases create own type/type wrapper (even if it is a trivial 1-to-1 type alias)
* prefer TS type unions over enums; use enums only when name usage is really better than direct value usage (e.g. when values are meaningless - e.g. API error codes, etc.)

## Naming

* names should be completely self-explanatory without need to know context (e.g. file name should explain everything, without need to know folder name where file is allocated)
* avoid types with name that contains `model` (due to the model can refer to OOP - data+logic inside which is not ok for REDUX)

## State

* prefer NGRX entities
* keep state structure as flat as possible (avoid nested data structures)
* normalize data in the store
* avoid parametrized NGRX selectors, especially selector factories
* avoid meta-reducers
* facades should be stateless
* never subscribe in facades (if you need that - then there are good chances that something goes non-NGRX way)
* store (facades) is always injected into containers, guards, interceptors and rarely injected into other services (if you do so - then there are good chances that something goes non-NGRX way, must be a strong reason for the case)
* keep every single selector in dedicated file, reexport selectors via query object in index file

## Components

* prefer single component modules
* best place to declare component (import component module) is feature root module
* always separate container (smart) and presentational (dumb) components; never inject Store and other state-full services into dumb components; if you need some data from store almost everywhere (e.g. logged in user permissions) - then implement a custom directive with injected store, directive MUST use async pipe or run markForCheck (to trigger change detection upwards)
* never use styles/UI markup in container components
* do not use component input that accept RX streams (plain data only!)
* `OnPush` change detection for dumb components is a must
* avoid shared components module, prefer importing everything you need explicitely

## Services

* in most cases a service (regualr or guard) should be provided in feature core module
* most services must be stateless; connectors (API connectors, storage data access objects, etc.) can have state-full dependencies, but own code of such services must be stateless any way
* state-full services (with state-full dependencies) and services with side-effects (except store/facades) can only be injected into effects, never inject such services into components, facades and into other services (if you do so - then there are good chances that something goes non-NGRX way)
* services must be provided on the level (module) where they are used, avoid providing everything on app root level
* avoid plain functions (helpers), prefer stateless/side-effecft-less services which are injected via DI

## Routing

* keep routing as flat as possible, avoid encreasing router outlets nesting level unless there is a real reason for this deep nesting (if it is possible to implement required functionality without nested router outlet - then do not use it)
* avoid resolvers (due to type-unsafety)
* prefer relative router links over absolute router links, always use relative links when possible, especially in templates

## Misc

* TS strict mode and Angular full + strict template type checking is a must
* use import aliases for app and all features (remember more nested feature aliases should go first in tsconfig alias list because IDE intellisense uses first matching alias)
* use Angular environments only to identify dev/not-dev mode; config must be processed in another way, so that artifact can be used with any env once it is built and there is no need to rebuild the artifact just because of env is different
