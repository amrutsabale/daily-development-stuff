## one line e.g [amrutssssdasd...]

```
div {
  width: 300px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

## two line e.g

```
+--------------------+
|abcde feg hij   dkjd|
|jdis ajid dheu d ...|/*Here it's overflowed, so "..." is shown. */
+--------------------+

```

```
div {
  width: 300px;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
}
```
