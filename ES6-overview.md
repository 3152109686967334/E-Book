# ES6 - Modern JavaScript

ခြောက်ကြိမ်မြောက် တည်းဖြတ်မှုဖြစ်သည့်အတွက် ES6 ဟု အတိုကောက်ခေါ်၍ 2015 ခုနှစ်တွင် ဖန်တီးခဲ့သည့် အတွက် ECMAScript2015 ဟု ရံဖန်ရံခါ ခေါ်သည့် နည်းပညာသည် လက်ရှိ JavaScript (ES5) ကို အဆင့်မြှင့်တင်ထားသည့် နည်းပညာဖြစ်သည်။ ES6 တွင် ပါဝင်လာသည့် လုပ်ဆောင်ချက်များမှ အချို့ကို ရွေးထုတ် ဖော်ပြလိုက်ပါသည်။

## Block-scope Variable 

မူလ JavaScript တွင် `var` Keyword ကို အသုံးပြု၍ Variable များ ကြေငြာနိုင်သည်။ ထို Variable များသည် Function-scope သဘောသဘာဝ ရှိကြသည်။ ES6 တွင် `let` Keyword ကို အသုံးပြု၍ Block-scope Variable များ ကြေငြာအသုံးပြုနိုင်သည်။

```JavaScript
let i = 10
if(true) {
    let i = 5
}

console.log( i )         // => 10
```

နမူနာအရ `if` Block အတွင်းတွင် `i` Variable ကို ထပ်ဆင့်ကြေငြာ အသုံးပြုထားသော်လည် ထို Variable သည့် `if` Block နှင့်သာ သက်ဆိုင်သည့်အတွက် Block ပြင်ပရှိ `i` Variable ၏ မူလတန်ဖိုး မပြောင်းလဲခြင်း ဖြစ်သည်။

## Arrow Function

မူလ JavaScript တွင် Array `filter()` ၏ Callback အဖြစ် Nameless Function တစ်ခုကို ယခုကဲ့သို့ သတ်မှတ်ထားသည် ဆိုကြပါစို့။

```JavaScript
[1, 2, 3, 4].filter(function(v) {
    return v % 2
})
```

အလားတူလုပ်ဆောင်ချက်ကို ES6 ရေးထုံးတွင် အောက်ပါကဲ့သို့ ပြောင်းလဲ ရေးသားနိုင်သည်။

```JavaScript
[1, 2, 3, 4].filter( v => v % 2 )
```

ဤလုပ်ဆောင်ချက်ကို Arrow Function ဟုခေါ်သည်။ အခြေခံအားဖြင့် `function` Keyword ကို `=>` သင်္ကေတဖြင့် အစားထိုးလိုက်ခြင်း ဖြစ်၍ `return` Keyword ကို ဖယ်ထုတ်လိုက်ခြင်း ဖြစ်သည်။ ဝိုက်ကွင်းများ တွန့်ကွင်းများကို လိုအပ်သလို အသုံးပြု၍ အောက်ပါအတိုင်းလည်း ရေးနိုင်သည်။

```JavaScript
[1, 2, 3, 4].reduce( (c, v) => {
    return c + v
})
```

## Rest Parameter

Function Parameter များကို သတ်မှတ်ပမာဏထက်ပို၍ အလွယ်တစ်ကူ လက်ခံနိုင်စေသည့် ရေထုံးဖြစ်သည်။

```JavaScript
function test(a, b, ...c) {
    console.log( c )
}

test( 1, 2, 3, 4, 5 )        // => [3, 4, 5]
```

နမူနာအရ `test()` Function သည် သတ်မှတ်ပမာဏထက် ပိုပေးလိုက်သည့် Parameter များကို Array တစ်ခုအနေနှင့် `c` Parameter ၏ တန်ဖိုးအဖြစ် သတ်မှတ်ပေးသွားခြင်း ဖြစ်သည်။

## Spread Operator

Array, String စသည့် Iteratable Value များကို ခွဲဖြန့်ပေးနိုင်သည့် လုပ်ဆောင်ချက်ဖြစ်သည်။

```JavaScript
var alpha = [ 'a', 'b', 'c' ]
var num = [1, 2, 3]
console.log([ ...alpha, ...num ])    // => ['a', 'b', 'c', 1, 2, 3]
```

နမူနာအရ ခွဲဖြန့်လိုက်သည့် တန်ဖိုးများကို Array တစ်ခုထဲတွင် စုစည်းလိုက်သည့်အတွက် Array နှစ်ခုကို တွဲဆက်လိုက်သကဲ့သို့ တူညီသော ရလဒ်ကို ရရှိခြင်းဖြစ်သည်။

## String Interpolation

String များတွင် Variable များ Property များကို Concat လုပ်၍ တွဲဆက်နေရန် မလိုအပ်တော့ပဲ တိုက်ရိုက် ထည့်သွင်းအသုံးပြုနိုင်စေသည့် လုပ်ဆောင်ချက် ဖြစ်သည်။

```JavaScript
var user = { name: 'Bob', age: 22 }

console.log( `My name is ${user.name}, I'm ${user.age} years old.` )

// => My name is Bob, I'm 22 years old.
```

String ကို Single Quote / Double Quote များနှင့် မရေးသားပဲ Backtick အဖွင့်အပိတ်ဖြင့် ရေးသားသည်ကို သတိပြုပါ။

## Property Shorthand

မူလ JavaScript တွင် ဤကဲ့သို့သော အခြေအနေများ မကြာခဏ ကြုံရတတ်သည်။

```JavaScript
var name = 'Bob'
var age = 22
var user = {
    name: name,
    age: age,
    say: function() {
        return 'Hello'
    }
}
```

Property Name နှင့် Value အဖြစ်အသုံးပြုလိုသည့် Variable အမည်တို့ တူညီနေခြင်းဖြစ်သည်။ ဤကဲ့သို့ အခြေအနေမျိုးအတွက် ES6 တွင် အောက်ပါအတိုင်း အတိုကောက် ရေးနိုင်သည်။

```JavaScript
var name = 'Bob'
var age = 22
var user = {
    name,
    age,
    say() {
        return 'Hello'
    }
}
```

Method ကိုလည်း function Keyword မပါဝင်တော့ပဲ အတိုကောက် ရေးသားထားသည်ကို သတိပြုပါ။

## Class

မူလ JavaScript တွင် Object များတည်ဆောက်ရန် Object Constructor (Function) သို့မဟုတ် JSON ကို အသုံးပြုရသည်၊ Class ရေးထုံး မပါဝင်ပါ။ ES6 တွင် Class ရေးထုံး ပါဝင်လာသည်။

```JavaScript
class Animal {
    constructor(legs, wings) {
        this.legs = legs
        this.wings = wings
    }

    say() {
        return 'Hello, World'
    }
}

class Dog extends Animal {
    constructor(legs) {
        super(legs, 0)
    }

    say() {
        return "I'm a good boi"
    }

}
```

Inheritance အတွက် OOP Language အများစုကဲ့သို့ `extends` Keyword ကို ဆက်လက်အသုံးပြု၍ Method များ ကြေငြာရန် `function` Keyword အသုံးပြုခြင်း မရှိသည်ကို သတိပြုရပေမည်။

## Module

မူလ JavaScript တွင် Module Loader လုပ်ဆောင်ချက် ပါဝင်ခြင်းမရှိပါ။ ထို့ကြောင့် သီးခြား ခွဲခြားထားသည့် JavaScript Code များကို တွဲဖက် အလုပ်လုပ်နိုင်စေရန် `<script src="">` HTML Element ၏ အကူအညီကို ရယူရသည်။ ES6 တွင် Module လုပ်ဆောင်ချက် ပါဝင်လာခဲ့ပြီဖြစ်သည်။

```JavaScript
// A Module (math.js)
exports var PI = 3.1416

exports function area(r) {
    return PI * r * r
}
```

```JavaScript
// Another Module (app.js)
import { PI, area } from './math.js'

console.log( area(8) )    // => 201.0624
```

`math.js` Module ၏ လုပ်ဆောင်ချက်များကို `app.js` က Import လုပ်ယူ အသုံးပြုထားခြင်းဖြစ်သည်။

______

Promise, Proxy, Generator စသည့် အခြား စိတ်ဝင်စားဖွယ် လုပ်ဆောင်ချက်များလည်း ကျန်ရှိပေသေးသည်။ အောက်ပါလိပ်စာတွင် ဆက်လက်လေ့လာနိုင်သည်။

http://es6-features.org

ယနေ့အချိန်တွင် Internet Explorer မှလွဲ၍ Chrome, Firefox, Edge စသည့် Modern Browser အများစုတွင် ES6 လုပ်ဆောင်ချက် အများအပြားကို ပံ့ပိုးပေးနေပြီဖြစ်သည်။ အသေးစိတ်ကို အောက်ပါဇယားတွင် စီစစ် လေ့လာနိုင်ပါသည်။

https://kangax.github.io/compat-table/es6/