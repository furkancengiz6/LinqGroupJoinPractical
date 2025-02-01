# LINQ Group Join ile Öğrenci ve Sınıf Listesi

## 📌 Proje Açıklaması
Bu proje, C# dilinde **LINQ Group Join** kullanarak bir **öğrenci ve sınıf listesini** ilişkilendirir.

- **Amaç:** Öğrencileri sınıflarıyla eşleştirerek, her sınıfa ait öğrencileri listelemek.
- **Kullanılan Teknoloji:** C# ve LINQ

---

## 📂 Proje Yapısı

- **`Student` Sınıfı:** Öğrenci bilgilerini içerir.
- **`Class` Sınıfı:** Sınıf bilgilerini içerir.
- **LINQ Group Join İşlemi:** Öğrenciler ve sınıflar arasında grup birleştirme işlemi yaparak çıktı oluşturur.

---

## 🚀 Kullanım

### 1️⃣ **Kodun Çalıştırılması**
Projeyi çalıştırmak için aşağıdaki adımları takip edin:

1. **C# geliştirme ortamınızı (ör. Visual Studio) açın.**
2. **Yeni bir C# Console Application oluşturun.**
3. **Aşağıdaki kodu `Program.cs` dosyanıza yapıştırın:**

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    static void Main()
    {
        // Öğrenci listesi
        List<Student> students = new List<Student>
        {
            new Student { StudentId = 1, StudentName = "Ali", ClassId = 1 },
            new Student { StudentId = 2, StudentName = "Ayşe", ClassId = 2 },
            new Student { StudentId = 3, StudentName = "Mehmet", ClassId = 1 },
            new Student { StudentId = 4, StudentName = "Fatma", ClassId = 3 },
            new Student { StudentId = 5, StudentName = "Ahmet", ClassId = 2 }
        };

        // Sınıf listesi
        List<Class> classes = new List<Class>
        {
            new Class { ClassId = 1, ClassName = "Matematik" },
            new Class { ClassId = 2, ClassName = "Türkçe" },
            new Class { ClassId = 3, ClassName = "Kimya" }
        };

        // Group Join işlemi
        var classGroups = from c in classes
                          join s in students on c.ClassId equals s.ClassId into studentGroup
                          select new
                          {
                              ClassName = c.ClassName,
                              Students = studentGroup
                          };

        // Sonuçları yazdır
        foreach (var group in classGroups)
        {
            Console.WriteLine($"Sınıf: {group.ClassName}");
            foreach (var student in group.Students)
            {
                Console.WriteLine($" - {student.StudentName}");
            }
            Console.WriteLine();
        }
    }
}

// Öğrenci sınıfı
class Student
{
    public int StudentId { get; set; }
    public string StudentName { get; set; }
    public int ClassId { get; set; }
}

// Sınıf sınıfı
class Class
{
    public int ClassId { get; set; }
    public string ClassName { get; set; }
}
```

4. **Uygulamayı çalıştırın ve aşağıdaki gibi bir çıktı alacaksınız:**

```
Sınıf: Matematik
 - Ali
 - Mehmet

Sınıf: Türkçe
 - Ayşe
 - Ahmet

Sınıf: Kimya
 - Fatma
```

---

## 🎯 Öğrenilen Konular
✅ **LINQ kullanarak Group Join işlemi yapmak**
✅ **Liste (List<T>) veri yapısını kullanmak**
✅ **Anonim türler ile verileri gruplamak**
✅ **Foreach döngüsü ile gruplandırılmış verileri yazdırmak**

---

## 🔥 Katkıda Bulunma
Projeye katkıda bulunmak isterseniz, pull request gönderebilir veya önerilerinizi paylaşabilirsiniz. 😊

---

**📌 Hazırlayan:** [Adınızı Buraya Yazın]

