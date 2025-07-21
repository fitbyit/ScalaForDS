# Practical 2
## Calculate mean, median, and mode of a list of numbers. Implement basic statistical calculations using Scala collections.
---
### Code :
> Scala code snippet
```scala
def mean(numbers: List[Double]): Double = {
  if numbers.isEmpty then Double.NaN
  else numbers.sum / numbers.length
}

def median(numbers: List[Double]): Double = {
  if numbers.isEmpty then return Double.NaN
  
  val sorted = numbers.sorted
  val n = sorted.length
  if n % 2 == 1 then sorted(n / 2)
  else (sorted(n / 2 - 1) + sorted(n / 2)) / 2.0
}

def mode(numbers: List[Double]): List[Double] = {
  if numbers.isEmpty then return List()
  
  val frequencyMap = numbers.groupBy(identity).mapValues(_.size)
  val maxFrequency = frequencyMap.values.max
  frequencyMap.collect {
    case (num, freq) if freq == maxFrequency => num
  }.toList.sorted
}

@main def calculateStatistics(): Unit = {
  val numbers = List(1.0, 3.0, 2.0, 2.0, 4.0, 3.0, 3.0, 5.0)
  
  println(s"Numbers: ${numbers.mkString(", ")}")
  println(f"Mean: ${mean(numbers)}%.2f")
  println(f"Median: ${median(numbers)}%.2f")
  println(s"Mode: ${mode(numbers).mkString(", ")}")
}
```

