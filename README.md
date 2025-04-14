# Pemmob1_MutiaraDewi

## Tampilan Aplikasi

1). Pada Activity_Main
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <LinearLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        android:padding="16dp"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <Button
            android:id="@+id/buttonToast"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="@string/button_toast"
            android:background="@color/black"
            android:textStyle="bold"
            android:textSize="18sp"/>
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="150dp"
            android:layout_gravity="center"
            android:src="@drawable/pandaa"/>
        <EditText
            android:id="@+id/etPhone"
            android:hint="Masukkan No HP"
            android:inputType="phone"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="16dp"/>
        <TextView
            android:id="@+id/textNum"
            android:layout_width="match_parent"
            android:layout_height="300dp"
            android:textSize="200sp"
            android:text="@string/num"
            android:gravity="center"
            android:textColor="@color/white"
            android:background="@color/black"/>

            <Button
                android:id="@+id/btnDate"
                android:text="Pilih Tanggal"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content" />

            <Button
                android:id="@+id/btnTime"
                android:text="Pilih Waktu"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content" />

        <Button
            android:id="@+id/buttonCount"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="@string/button_count"
                android:textStyle="bold"
                android:backgroundTint="@color/kuning"
                android:textSize="18sp"/>

    </LinearLayout>

</androidx.constraintlayout.widget.ConstraintLayout>

Penjelasan
Dalam Activity_Main terdapat beberapa layout yang berisi:
-	Button Toast untuk menampilkan nomor HP di Toast
-	ImageView untuk menampilkan gambar yang di input (panda)
-	EditText (etPhone) untuk menginput nomor HP
-	TextView (textNum) untuk menampilkan angka counter
-	Button Date & Time untuk memilih tanggal dan waktu
-	Button Count untuk menambahkan angka counter


2). Pada MainActivity
package com.example.tugas2

import android.app.DatePickerDialog
import android.app.TimePickerDialog
import android.os.Bundle
import android.widget.*
import androidx.appcompat.app.AppCompatActivity
import java.util.*

class MainActivity : AppCompatActivity() {

    private lateinit var etPhone: EditText
    private lateinit var btnDate: Button
    private lateinit var btnTime: Button
    private lateinit var textNum: TextView
    private lateinit var buttonToast: Button
    private lateinit var buttonCount: Button

    private var countValue = 0

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Inisialisasi komponen
        etPhone = findViewById(R.id.etPhone)
        btnDate = findViewById(R.id.btnDate)
        btnTime = findViewById(R.id.btnTime)
        textNum = findViewById(R.id.textNum)
        buttonToast = findViewById(R.id.buttonToast)
        buttonCount = findViewById(R.id.buttonCount)

        // Tombol Toast
        buttonToast.setOnClickListener {
            val phone = etPhone.text.toString()
            Toast.makeText(this, "Nomor HP: $phone", Toast.LENGTH_SHORT).show()
        }

        // Tombol Date Picker
        btnDate.setOnClickListener {
            showDatePicker()
        }

        // Tombol Time Picker
        btnTime.setOnClickListener {
            showTimePicker()
        }

        // Tombol Count
        buttonCount.setOnClickListener {
            countValue++
            textNum.text = countValue.toString()
        }
    }

    private fun showDatePicker() {
        val calendar = Calendar.getInstance()
        val year = calendar.get(Calendar.YEAR)
        val month = calendar.get(Calendar.MONTH)
        val day = calendar.get(Calendar.DAY_OF_MONTH)

        val datePickerDialog = DatePickerDialog(this,
            { _, yearPicked, monthPicked, dayOfMonth ->
                Toast.makeText(
                    this,
                    "Tanggal: $dayOfMonth/${monthPicked+1}/$yearPicked",
                    Toast.LENGTH_SHORT
                ).show()
            },
            year, month, day)
        datePickerDialog.show()
    }

    private fun showTimePicker() {
        val calendar = Calendar.getInstance()
        val hour = calendar.get(Calendar.HOUR_OF_DAY)
        val minute = calendar.get(Calendar.MINUTE)

        val timePickerDialog = TimePickerDialog(this,
            { _, hourOfDay, minutePicked ->
                Toast.makeText(
                    this,
                    "Waktu: $hourOfDay:$minutePicked",
                    Toast.LENGTH_SHORT
                ).show()
            },
            hour, minute, true)
        timePickerDialog.show()
    }
}

Penjelasan
Dalam MainActivity.kt hal pertama yang harus dilakukan adalah
-	Inisialisasi komponen menggunakan findViewById
-	ButtonToast untuk mengambil isi etPhone lalu di tampilkan pada Toast
-	btnDate untuk menampilkan DatePicker lalu hasilnya pada Toast
-	btnTime untuk menampilkan TimePicker beri hasilnya ke Toast
-	buttonCount untuk menambahkan nilai countValue lalu tampilkan pada textNum

Google Dokumen : [Link PDF]([https://google.com](https://drive.google.com/drive/folders/1vbAip2B-1Q6iZKBDMFgJfzh-oVGEp-0d?usp=drive_link))
