https://www.youtube.com/watch?v=2AMRTAFSh98

### intl api | I18N

#### 숫자 간결하게 나타내기

```js
const views = 9744642;
const formatter = new Intl.NumberFormat('ko');

formatter.format(views); //9,744,642

const formatter = new Intl.NumberFormat('ko', { notation: 'compact ' }); // 974만

const formatter = new Intl.NumberFormat('ko', { notation: 'compact', compactDisplay: 'long' });
```

### 가격 간결하게 나타내기

```js
const price = 10000;

const formatter = new Intl.NumberForamt('ko'{
    style:'currency',
    curreny:"krw',
    notation:'compact'
});

formatter.format(price) 1만

노테이션없애면 풀어서보여줌

ko / en-US / currency : usd
```

### 상대시간 똑똑하게 나타내기

```js
const formatter = new Intl.RelativeTimeFormat('en');

formatter.format(1, 'day'); // -1 하면 하루전

{
  numeric: 'auto';
}
로하면 tomorrow 같이 바뀜

day , hour , secoend 같이 여러 옵션있음


const today = new Date()

const started = new Date(1995,5,6)

const dayPassed = Math.ceil((started-today)/(1000*60*60*24 ))

formatter.format(dayPassed,'day')

```

### 날짜 시간 포맷

```js
const date = new Date();

date.toLocaleDateString('ko', {
  dateStyle: 'full',
  timeStyle: 'long',
  hour"numeric"//long,short
});
```

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl
