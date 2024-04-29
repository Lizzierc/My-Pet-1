# My-Pet-1
Assignment 2
package com.example.assignment2

import android.annotation.SuppressLint
import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.os.Parcel
import android.os.Parcelable
import android.widget.Button

class MainActivity() : AppCompatActivity() {

    @SuppressLint("MissingInflatedId")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        // Declare the views
        val next = findViewById<Button>(R.id.btnFeed)
        next.setOnClickListener {
            intent = Intent(this, MainActivity::class.java)
            startActivity(intent)
        }

    }

}

package com.example.assignment2

import android.annotation.SuppressLint
import android.os.Bundle
import android.view.animation.AlphaAnimation
import android.widget.Button
import android.widget.EditText
import android.widget.ImageView
import androidx.appcompat.app.AppCompatActivity



class MainActivity2 : AppCompatActivity() {


    private var petHealth = 100
    private var petHunger = 50
    private var petCleanliness = 50



    @SuppressLint("MissingInflatedId")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main2)

        // Get the button and text views
        val btnFeed =findViewById<Button>(R.id.btnFeed)
        val btnClean =findViewById<Button>(R.id.btnClean)
        val btnHappy =findViewById<Button>(R.id.btnHappy)
        val txtHunger =findViewById<EditText>(R.id.txtHunger_value)
        val txtHealth =findViewById<EditText>(R.id.txtHealth_value)
        val txtHappy =findViewById<EditText>(R.id.txtHappy)
        findViewById<ImageView>(R.id.petImage)

        // Set the initial text values
        txtHunger.setText(petHunger.toString())
        txtHealth.setText(petHealth.toString())
        txtHappy.setText(petHealth.toString())

        //Handle button clicks
        btnFeed.setOnClickListener {

            petHunger -= 10
            petHealth += 10
            petHunger += 5
            txtHunger.setText(petHunger.toString())


            btnClean.setText(petCleanliness.toString())
            petCleanliness += 10
            petHealth += 10

            btnClean.setText(petCleanliness)

        }
        btnClean.setOnClickListener {
            petCleanliness += 10
            petHealth += 10

            txtHealth.setText(petCleanliness.toString())


        }
        btnHappy.setOnClickListener {
            petHealth += 10
            petHunger += 5
            petCleanliness -= 5
            txtHappy.setText(petHealth.toString())

        }

    }

    private fun animateImageChange(imageView: ImageView, newImageResource: Int) {
        val animate = AlphaAnimation(0.0f, 1.0f)
        animate.duration = 500
        animate.fillAfter = true
        imageView.startAnimation(animate)
        imageView.setImageResource(newImageResource)



    }

}































