# Modul-5_Rekursif
Struktur Data

# Modul-5_Struktur-Data
Rekursif

Sebuah perulangan di dalam sebuah program namun, perulangan ini sangat berbeda seperti while dan for, 

Walaupun fungsinya sama yaitu looping. Letak perbedaannya adalah dari cara kerjanya, 

jika for dan while merupakan sebuah looping yang menggunakan sebuah boolean, 

maka pada rekursif ini terjadi pada sebuah fungsi atau metode yang memanggil dirinya sendiri.

Iteratif merupakan penyelesaian permasalahan dengan perulangan, menggunakan syntax for atau while (pada Python).

      def factorialIteratif(bilangan):
            if bilangan <=1:
                return(1)
            else:
                temp=bilangan
                hasil=1
                while temp>1:
                    hasil=hasil*temp
                    temp=temp-1
                return(hasil)

        print(factorialIteratif(4))

---------------------------------------------------------------------------------------------------------------------
Perhitungan faktorial dengan cara rekursif

      def factorialRekursif(bilangan):
            if bilangan <=1:
                return(1)
            else:
                return(bilangan * factorialRekursif(bilangan-1))

        data=factorialRekursif(4)
        print(data)

Berikut beberapa aturan dalam teknik pemrograman rekursif:

1.	Fungsi rekursif harus memiliki base case, base case inilah yang berfungsi untuk menghentikan pemanggilan terus menerus fungsi rekursif

2.	fungsi rekursif harus memiliki sintaks yang dapat merubah state dari permasalahan, sehingga semakin lama solusi permasalahan menuju base case yang sudah dibuat

3.	Fungsi rekursif harus memanggil dirinya sendiri

-----------------------------------------------------------------------------------------------------------------
Menghitung triangular numbers melalui teknik iterative

      def triangularNumbers1(n):
            total=0
            temp=n
            while temp>=1:
                total+=temp
                temp-=1
            return(total)

        print(triangularNumbers1(2))

Fungsi rekursif dari triangular numbers.

      def triangularNumbers2(n):
            if n==1:
                return(1)
            else:
                return (n + triangularNumbrs2(n-1))

------------------------------------------------------------------------------------------------------------------------------
Konversi Bilangan

Suatu proses dimana satu system bilangan tertentu akan dijadikan bilangan lain. Bilangan integer ini dikenal juga sebagai bilangan dengan base 10 (desimal), sehingga memiliki kemungkinan character angka dari 0 s.d 9.

      def konversiDesimal(bilangan,base):
                  charBilangan='0123456789ABCDEF'
                  if bilangan<base:
                      return(charBilangan[bilangan])
                  else:
                      temp=bilangan//base
                      ind=bilangan % base
                      print(type(temp),temp,type(ind),ind)
                      return(konversiDesimal(temp,base)+charBilangan[ind])

              konversiDesimal(5,2)

---------------------------------------------------------------------------------------------------------------------------
Towers of Hanoi

Pendeta memerintahkan para pekerjanya untuk memindahkan 64 piringan emas dengan ukuran yang berbeda-beda dari satu tiang ke tiang lainnya. Syarat memindahkan piringan emas: 

1. piringan emas harus dipindahkan satu persatu 

2. piringan emas berukuran kecil harus berada diatas piringan emas berukuran besar.


Dalam algoritma :
1.	Pindahkan piringan sebanyak n-1n−1 dari tiang awal ke tiang bantuan.

2.	Pindahkan piringan ke nn dari tiang awal ke tiang tujuan.

3.	Pindahkan piringan sebanyak n-1n−1 dari tiang bantuan ke tiang tujuan, melalui tiang awal

            def towers(n,awal,bantuan,tujuan):
                        if n==1:
                            print("Piringan - 1 dari-", awal,"ke-",tujuan)
                        else:
                            towers(n-1,awal,tujuan,bantuan)
                            print("Piringan -",n, "dari-",awal,"ke-", tujuan)
                            towers(n-1,bantuan,awal,tujuan

                    towers(4,'A','B','C')


Dalam teknik pemrograman rekursif menggunakan modul Turle

      import turtle
              my_turtle = turtle.Turtle()
              my_win = turtle.Screen()

              def draw_spiral(my_turtle, line_len):
                  if line_len > 0:
                      my_turtle.forward(line_len)
                      my_turtle.right(90)
                      draw_spiral(my_turtle, line_len - 5)

              draw_spiral(my_turtle, 90)
              my_win.exitonclick()

-----------------------------------------------------------------------------------------------------------------------------
Fractal

Cabang matematika dan memiliki banyak kesamaan dengan teknik rekursif. Fraktal memiliki bentuk dasar, dan bentuk dasar ini dikembangkan secara berulang terus menerus.

Pembuatan fractal secara rekursif dengan modul Turtle.

      import turtle
                          def tree(branch_len, t):
                              t.speed('slowest')
                              if branch_len > 5:
                                  t.forward(branch_len)
                                  t.right(20)
                                  tree(branch_len - 15, t)
                                  t.left(40)
                                  tree(branch_len - 15, t)
                                  t.right(20)
                                  t.backward(branch_len)

                          def main():
                              my_win = turtle.Screen()
                              t = turtle.Turtle()

                              t.shape("turtle")
                              t.left(90)
                              t.up()
                              t.backward(100)
                              t.down()
                              t.color("green")
                              tree(60, t)
                              my_win.exitonclick()
                          main()

---------------------------------------------------------------------------
Segitia Sierpinski 

Juga merupakan bentuk fraktal. Segitiga ini memiliki bentuk dasar (yaitu, suatu segitiga dan didalamnya terdapat empat buat segitiga dengan ukuran yang sama), dan bentuk dasar ini terus menerus dibangkitkan sampai derajat tertentu.

        import turtle
        def draw_triangle(points, color, my_turtle):   
            my_turtle.speed('slowest')
            my_turtle.fillcolor(color)
            my_turtle.up()
            my_turtle.goto(points[0][0],points[0][1])
            my_turtle.down()
            my_turtle.begin_fill()
            my_turtle.goto(points[1][0], points[1][1])
            my_turtle.goto(points[2][0], points[2][1])
            my_turtle.goto(points[0][0], points[0][1])
            my_turtle.end_fill()
        def get_mid(p1, p2):
            return ((p1[0] + p2[0]) / 2, (p1[1] + p2[1]) / 2)
        def sierpinski(points, degree, my_turtle):
            color_map = ["blue", "red" , "green", "white" , "yellow" ,"violet" , "orange"]
            draw_triangle(points, color_map[degree], my_turtle)
            if degree > 0:
                sierpinski([points[0],get_mid(points[0], points[1]), get_mid(points[0], points[2])], degree-1, my_turtle)
                sierpinski([points[1],get_mid(points[0], points[1]), get_mid(points[1], points[2])], degree-1, my_turtle)
                sierpinski([points[2],get_mid(points[2], points[1]), get_mid(points[0], points[2])], degree-1, my_turtle)

        def main():
            my_turtle = turtle.Turtle()
            my_win = turtle.Screen()
            my_points = [[-100, -50], [0, 100], [100, -50]]
            sierpinski(my_points, 2, my_turtle)
            my_win.exitonclick()

        main()

--------------------------------------------------------------------------------------------------------------------------------
Praktikum – modul 5 (file tugas praktikum modul 5 disertakan di dalam lampiran)

-------------------------------------------------------------------------------------------------------------------------------
Jawaban

      import turtle
      my_turtle = turtle.Turtle()
      my_win = turtle.Screen()

      def draw_square(my_turtle, line_len,a,banyak_level,b):
          if b<banyak_level+1:
              if a<4:
                  if line_len > 0:
                      my_turtle.forward(line_len/2)
                      my_turtle.right(90)
                      my_turtle.forward(line_len)
                      my_turtle.right(90)
                      my_turtle.forward(line_len/2)
                      my_turtle.right(90)
                      draw_square(my_turtle, line_len,a+1,banyak_level,b)
              else:
                  draw_square(my_turtle, line_len/2,0,banyak_level,b+1)

      draw_square(my_turtle, 200,0,1,0)
      my_win.exitonclick()
