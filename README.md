# DesignPatterns

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
