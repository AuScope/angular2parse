# angular2parse
Parse util for angular expressions:  html string -> angular template

**This is a fork of Articode's [angular2parse](https://github.com/articodeltd/angular2parse), adapted for Angular v12 - v19**

**Available from 'npmjs' https://www.npmjs.com/package/@auscope/angular2parse**

| Angular Version | Branch      |
|-----------------|-------------|
| v19             | upgrade-v19 |
| v18             | upgrade-v18 |
| v17             | upgrade-v17 |
| v16             | upgrade-v16 |
| v15             | upgrade-v15 |
| v14             | upgrade-v14 |
| v13             | upgrade-v13 |
| v12             | upgrade-v12 |


# install 
`npm install angular2parse`

```typescript 
// app.module.ts
@NgModule({
  imports: [Angular2ParseModule, ...],
  // ...
})
class AppModule {}
```
# usage 
```typescript
import { Parse } from 'angular2parse';

@Injectable()
class MyService {
  constructor(private parser: Parse) {}
  
  parseAngularString() {
    const expression = `{
	positions: track.positions,
	cornerType: getCornerType(),
	material: track.color,
	width : 200000.0 }`;

   const expressionEvalFn = this.parser.eval(expression)
  
   const context = {
      getCornerType: () => 'value',
      track: {
          positions: [1,2,3],
          color: 'red',
        }
      }
   };
    
   const result = expressionEvalFn(context);
   console.log(result);
   // {positions: [1,2,3], cornerType: 'value', material: 'red', width: 2000}
  
}

```

```
