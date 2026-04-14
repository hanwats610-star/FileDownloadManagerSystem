# 📥 File Download Manager System — Java

A multithreaded file download manager built in Java using `Callable`, `Future`, and `ExecutorService`.

---

## 🚀 What It Does

- Multiple files ko **concurrently (parallel)** download karta hai
- Thread pool use karta hai — max **4 threads** ek saath
- URL validate karta hai before downloading
- Destination folder automatically create karta hai agar exist na kare

---

## 🗂️ Project Structure

```
com.downloader/
├── DownloadTask.java       # Ek file download karne ka task (Callable)
├── DownloadUtils.java      # Helper methods (URL check, file save, folder verify)
├── DownloadManager.java    # Sab tasks manage karta hai (ExecutorService)
└── Main.java               # Entry point
```

---

## ⚙️ How It Works

```
URLs input → Validate → DownloadTask banao → Thread Pool mein submit → Parallel download → Result print
```

---

## 🧩 Key Concepts Used

| Concept | Kahan Use Hua |
|---|---|
| `Callable<String>` | `DownloadTask` — result return karta hai |
| `Future<String>` | Download ka result baad mein lene ke liye |
| `ExecutorService` | Thread pool manage karta hai |
| `invokeAll()` | Sab tasks ek saath parallel chalata hai |
| `HttpURLConnection` | URL validate + file download |
| `BufferedInputStream` | 4KB chunks mein file read karta hai |

---

## ▶️ How to Run

**1. Clone / Open in IntelliJ IDEA**

**2. Package structure set karo:**
```
src/com/downloader/
```

**3. `DownloadManager.java` mein URLs aur destination set karo:**
```java
String[] fileUrls = {
    "http://example.com/file1.zip",
    "http://example.com/file2.zip"
};
String destination = "/your/save/path";
```

**4. `DownloadManager` class run karo**

---

## 📦 Requirements

- Java 8 or above
- Internet connection (real URLs ke liye)
- No external libraries needed

---

## 📋 Sample Output

```
Starting download from: http://example.com/file1.zip
Starting download from: http://example.com/file2.zip
Download completed for: http://example.com/file1.zip
Download successful for http://example.com/file1.zip
```

---

## 📝 Notes

- `Thread.sleep(3000)` sirf simulation ke liye hai — real implementation mein `DownloadUtils.downloadFile()` use karo
- Thread pool size `NUM_THREADS = 4` hai, zarurat ke hisaab se change kar sakte ho
