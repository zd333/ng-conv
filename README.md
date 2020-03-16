# ng-conv

## Folder structure

```bash
├── app-component.ts
├── app-module.ts
├── app-core.module.ts
├── app-routing.module.ts
├── app-shared.module.ts
├── +state
│   ├── app-state.module.ts
│   ├── router-serializer.ts
│   ├── selectors
│   │   ├── index.ts
│   │   ├── some-auth.selector.ts
│   │   ├── another-auth.selector.ts.ts
│   │   ├── some-root.selector.ts
│   │   ├── another-root.selector.ts
│   │   └── some-compound.selector.ts
│   └── slices
│       ├── auth
│       │   ├── index.ts
│       │   ├── auth.actions.ts
│       │   ├── auth.effects.ts
│       │   ├── auth.reducer.ts
│       │   └── auth-state.facade.ts
│       └── root
│           ├── index.ts
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
│   ├── error-codes.enum.ts
│   ├── root-initial-state.constant.ts
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
└── sub-features
    ├── some-feature1
    │   ├── some-feature1.module.ts
    │   ├── some-feature1-core.module.ts
    │   ├── some-feature1-routing.module.ts
    │   ├── some-feature1-shared.module.ts
    │   ├── +state
    │   │   ├── index.ts    
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
        ├── some-feature2-routing.module.ts
        ├── +state
        │   ├── some-feature2-state.module.ts        
        │   ├── selectors
        │   │   ├── index.ts        
        │   │   ├── some-entity-y.selector.ts
        │   │   └── some-entity-z.selector.ts
        │   └── slices
        │       ├── entity-y
        │       │   ├── index.ts
        │       │   ├── entity-y.actions.ts        
        │       │   ├── entity-y.effects.ts
        │       │   ├── entity-y.reducer.ts
        │       │   └── entity-y-state.facade.ts
        │       └── entity-z
        │           ├── indexs.ts        
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
