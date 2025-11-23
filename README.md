# Why?
I don't like indirect dependencies coming with `stretchr/testify`.  
And I usually needed only fraction of its features.  
I searched for a simpler assert library and found [matryer/is](https://github.com/matryer/is), which is delicious.  
But it doesn't have JSON equality assertion (see [issues/59](https://github.com/matryer/is/issues/59))

This is fork adds `JSONEqual` method. (and removes pre-go1.7 support)

---

# is 
Professional lightweight testing mini-framework for Go.

* Easy to write and read
* [Beautifully simple API](https://pkg.go.dev/github.com/matryer/is) with everything you need: `is.Equal`, `is.True`, `is.NoErr`, and `is.Fail`
* Use comments to add descriptions (which show up when tests fail)

Failures are very easy to read:

![Examples of failures](https://github.com/matryer/is/raw/master/misc/delicious-failures.png)

### Usage

The following code shows a range of useful ways you can use
the helper methods:

```go
func Test(t *testing.T) {
	is := is.New(t)
	signedin, err := isSignedIn(ctx)
	is.NoErr(err)            // isSignedIn error
	is.Equal(signedin, true) // must be signed in
	body := readBody(r)
	is.True(strings.Contains(body, "Hi there"))
}
```

## Color

To turn off the colors, run `go test` with the `-nocolor` flag,
or with the env var [`NO_COLOR` (with any value)](https://no-color.org).

```
go test -nocolor
```

```
NO_COLOR=1 go test
```
