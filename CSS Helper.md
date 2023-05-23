
## Fill the height of the div's remaining screen space

```html
<html>
    <div id="box">
	    <div id="fixed">
	        Fixed Height
	    </div>
	    <div id="remaining">
	        Remaining Height
	    </div>
    </div>
</html>
```

```css
#box {
  display: flex;
  flex-flow: column;
  height: 100%;
}

#fixed {
  height: 80px;
  background-color: rgb(0, 255, 255);
}

#remaining {
  background-color: #6a9cff;
  flex-grow : 1;
}
```
