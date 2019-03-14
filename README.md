# Cancelling Preloading of Images

Experiment to understand which browser support cancelling preloading
of images with two differerent techniques:

## Using `Image`

```javascript
const i = new Image();
i.src = url;
setTimeout(() => {
  i.src = "";
});
```

## Using `XMLHttpRequest`

```javascript
const r = new XMLHttpRequest();
r.open("get", url, true);
r.send();
setTimeout(() => {
  i.abort();
});
```

According to [@stereobooster's
`react-ideal-image`](https://github.com/stereobooster/react-ideal-image/blob/master/introduction.md#cancel-download) the first technique (using <code>img = new Image(); img.src = ""</code>) doesn't work in <b>Mobile Safari</b>. That's a hugely popular browser so it's important to test if that's true.

The purpose of this experiment is to help:
[github.com/peterbe/autocomplete-with-images](https://github.com/peterbe/autocomplete-with-images)

## To run

```
npx serve -s
```

Then open `http://localhost:5000`

Press the two buttons and see what happens.
Ideally the image should not load!
