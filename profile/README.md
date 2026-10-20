<p align="center"><img src="https://raw.githubusercontent.com/go-bignum/brand/main/social/go-bignum.png" alt="go-bignum" width="720"></p>

# go-bignum

🌐 **[Website](https://go-bignum.github.io)** · 📚 **[Documentation](https://go-bignum.github.io/docs/)**

**Arbitrary precision in pure Go (CGO=0): correctly rounded elementary functions and constants on `math/big.Float`, and the oracle harness that checks them.**

Each function returns the exact result rounded to the receiver's precision in
the receiver's rounding mode, in all six modes, with `z.Acc()` telling on which
side of the exact value it lies: the MPFR contract. Every approximation is a
rigorous enclosure evaluated by Ziv's strategy, and the tests replay golden
fixtures certified with [mpmath](https://mpmath.org) at high precision, with
fuzzing against the package's own oracle. The library is in development and has
no release tag yet.

```go
z := new(big.Float).SetPrec(113).SetMode(big.ToNearestEven)
bigfloat.Exp(z, x) // e^x, correctly rounded to 113 bits
z.Acc()            // big.Below / big.Exact / big.Above: the side of the exact value
```

## Repositories

| Repo | What it is |
|------|------------|
| [**bigfloat**](https://github.com/go-bignum/bigfloat) | in development, no release tag yet: roots, exponentials and logarithms, trigonometric and hyperbolic functions, `Pow` and the constants π, e, ln 2, ln 10 and γ on `big.Float`, correctly rounded at any precision and in all six rounding modes; the `oracle` package drives mpmath from Go for correctly rounded reference values and golden fixtures |
| [**docs**](https://github.com/go-bignum/docs) | the documentation site (Hugo + Hextra), served at [/docs/](https://go-bignum.github.io/docs/) |
| [**go-bignum.github.io**](https://github.com/go-bignum/go-bignum.github.io) | the landing page (Hugo) |
| [**brand**](https://github.com/go-bignum/brand) | logo, icons and social images |

`bigfloat` needs Go 1.27.1 or later and has no dependencies; its fixtures run
on amd64, arm64, 386, arm, riscv64, loong64, ppc64le and s390x in CI.
