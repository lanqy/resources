# 通过代数数据类型和模式匹配进行语言比较：Koka，Rust，Haxe，Swift，Elm，PureScript，Haskell，OCaml，ReasonML，Kotlin，Scala，Dotty，Ruby，TypeScript

## 代数数据类型

### Wood

```wood
type color {
  Red
  Green
  Blue
  Rgb( r : int, g : int, b: int )
}
```

或

```wood
type color {
  Red; Green; Blue; Rgb( r : int, g : int, b: int )
}
```

### rust 

```rust
enum Color {
 Red,
 Green,
 Blue,
 Rgb { r: u8, g: u8, b: u8 }
}
```

### Haxe 

```haxe
enum Color {
  Red;
  Green;
  Blue;
  Rgb(r: Int, g: Int, b: Int);
}
```

### swift


```swift
enum Color {
  case Red, Green, Blue, Rgb(r: Int, g: Int, b: Int)
}
```

### Science

```science
type Color = Red | Green | Blue | Rgb { r: Int, g: Int, b: Int }
```

### PureScript

```purescript
data Color = Red | Blue | Green | Rgb{ r :: Int, g :: Int, b :: Int }
```

### Haskell

```haskell
data Color = Red | Green | Blue | Rgb {r :: Int, g :: Int, b :: Int}
```

### OCaml

```ocaml
type rgb = { r: int; g: int; b: int }
type color = Red | Green | Blue | Rgb of rgb
```

### ReasonML

```ocaml
type rgb = { r: int, g: int, b: int };
type color =
  | Red
  | Green
  | Blue
  | Rgb(rgb);
```

### Kotlin

```kotlin
sealed class Color {
    object Red: Color()
    object Green: Color()
    object Blue: Color()
    class Rgb(val r: Int,val  g: Int,val  b: Int): Color()
}
```

### Scala

```scala
sealed trait Color

final case object Red extends Color
final case object Green extends Color
final case object Blue extends Color
final case class Rgb(r: Int, g: Int, b: Int) extends Color
```

### Dotty

```dotty
enum Color {
  case Red
  case Green
  case Blue
  case Rgb(r: Int, g: Int, b: Int)
}
```

### TypeScript

```typescript
type Color = Red | Green | Blue | Rgb;
const enum ColorKind {
  Red = "Red",
  Green = "Green",
  Blue = "Blue",
  Rgb = "Rgb"
}

interface Red {
    kind: ColorKind.Red;
}

interface Green {
    kind: ColorKind.Green;
}

interface Blue {
    kind: ColorKind.Blue;
}

interface Rgb {
    kind: ColorKind.Rgb;
    r: number;
    g: number;
    b: number;
}
```

### Ruby

```ruby
module Color
  Red = 1
  Green = 2
  Blue = 3
  Rgb = Struct.new(:r, :g, :b)
end
```

## 感想

### 符号

Koka, Rust, Haxe, Elm: 非常好
Dotty, Swift, PureScript, Haskell, OCaml: 比较好
Ruby: 一般
Kotlin: 很难写
Scala: 写起来很难
