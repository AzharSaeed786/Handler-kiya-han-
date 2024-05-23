# Handler-kiya-han-
Android me Handler ek component hai jo thread ki MessageQueue se messages aur runnables ko manage karta hai. Ye khas tor par threads ke darmiyan communication aur UI updates ke liye use hota hai. Aam tor par iska istemal background threads se main thread (jo UI ko handle karta hai) pe updates bhejne ke liye hota hai.

Key Points:
Message Handling: Handler messages aur runnable objects ko handle karta hai jo thread ki MessageQueue me hote hain.
Thread Communication: Background threads se main thread pe safely UI updates karne ke liye Handler use hota hai.
Task Scheduling: Handler ka istemal tasks ko future me execute karne ke liye bhi hota hai, jaise postDelayed method.
Misaal:
Agar aapko network se data fetch karna ho aur us data ko UI pe display karna ho, to aap Handler ka istemal kar sakte hain:

Example Code:
kotlin
Copy code
val mainHandler = Handler(Looper.getMainLooper())

Thread {
    val data = performNetworkOperation() // Background thread me data fetch karna

    mainHandler.post {
        textView.text = data // Main thread pe UI update karna
    }
}.start()

fun performNetworkOperation(): String {
    Thread.sleep(2000) // Delay simulate karna
    return "Network se data fetched"
}
Explanation:
Handler ko main thread pe Looper.getMainLooper() ke sath create kiya gaya hai.
Background thread data fetch karta hai aur mainHandler.post ka istemal karte hue main thread pe data post karta hai jo TextView ko update karta hai.
Conclusion:
Handler aur Looper Android me thread communication aur UI updates ko manage karte hain, ensuring ke tasks correct thread pe execute hon aur application smoothly operate kare.

