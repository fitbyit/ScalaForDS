# Practical 3
## Generate a random dataset of 10 numbers and calculate its variance and standard deviation.
---

### Code :

> Scala code snippet
```scala
import scala.util.Random
import scala.math.sqrt

@main
def main() : Unit = 
  val seed = 42L
  val rng = new Random(seed)  
  val dataset = List.fill(10)(rng.between(0, 100).toDouble)
  //var dataset = List(113,146.5,132,70.5,121,55).map(_.toDouble)

  println(s"Generated dataset: ${dataset.mkString(", ")}")

  // Calculate mean
  val mean = dataset.sum / dataset.length

  // Calculate variance
  val variance = (dataset.map(x => math.pow(x - mean, 2)).sum) / (dataset.length-1)

  // Calculate standard deviation
  val stdDev = sqrt(variance)

  // Results 
  println(f"Mean: $mean")
  println(s"Variance: $variance")
  println(s"Standard Deviation: $stdDev")
```
