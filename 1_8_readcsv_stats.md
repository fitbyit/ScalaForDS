## Practical 8
### Read a CSV file and calculate basic statistics for each numeric column. Use the scala-csv library or similar tools
---

## build.sbt
 > This `build.sbt` defines the project's settings, dependencies, and resolvers.

```scala
libraryDependencies += "com.github.tototoshi" %% "scala-csv" % "1.3.10"
```
---

## Code
> Scala code snippet
```scala
import com.github.tototoshi.csv._
import java.io.File

@main
def main() : Unit =
  val reader = CSVReader.open(new File("data.csv"))
  val allRows = reader.allWithHeaders()
  reader.close()
  
  val subjects = List("Math", "Science", "English")
  
  subjects.foreach { subject =>
      val scores = allRows.flatMap(row => row.get(subject).map(_.toDouble))
      val avg = scores.sum / scores.size
      val min = scores.min
      val max = scores.max
  
      println(s"$subject Stats:")
      println(f"  Average: $avg%.2f")
      println(f"  Minimum: $min%.2f")
      println(f"  Maximum: $max%.2f")
  }
```
