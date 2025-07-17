# DesignPatterns
## Builder
### 1. Builder Design Pattern
The Builder Design Pattern is a creational software design pattern used to construct complex objects step by step. It separates the construction of an object from its representation, allowing the same construction process to create different representations.

#### Purpose
1. Decouples object construction from its representation.
2. Useful when an object must be created with many possible configurations or optional parameters.
3. Helps avoid telescoping constructors (constructors with many arguments).

class Animal private constructor(
    private val legs: Int,
    private val voiceTone: String,
    private val weight: Double,
    private val height: Int
) {

    fun showDetails() {
        println("legs: $legs, speakTone: $voiceTone, weight: $weight, height: $height")
    }

    class Builder {
        private var legs  = 4
        private var voiceTone = "bark"
        private var weight = 26.8
        private var height = 130 // in cm

        fun setLegs(legs: Int) = apply { this.legs = legs }

        fun setSpeak(voiceTone: String): Builder {
            this.voiceTone = voiceTone
            return this
        }

        fun setWeight(weight: Double): Builder {
            this.weight = weight
            return this
        }

        fun setHeight(height: Int) = apply { this.height = height }

        fun build(): Animal {
            return Animal(legs, voiceTone, weight, height)
        }
    }

}

fun main() {
    val dog = Animal.Builder()
        .setLegs(4)
        .setSpeak("Bho bho")
        .setWeight(60.0)
        .setHeight(120)
        .build()

    dog.showDetails()
}

