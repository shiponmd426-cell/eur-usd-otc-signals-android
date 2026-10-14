# EUR/USD OTC Signals — Android wrapper source

এই প্রজেক্টটি Android WebView অ্যাপ, যা আপনার প্রকাশিত ড্যাশবোর্ডটি Android অ্যাপের ভেতরে খুলবে।

**ড্যাশবোর্ড:** https://eur-usd-otc-signals-shipon1.vercel.app

## APK তৈরি করার উপায়

1. কম্পিউটারে Android Studio ইনস্টল করুন।
2. Android Studio থেকে `EurUsdOtcSignalsAndroid` ফোল্ডারটি Open করুন।
3. Gradle Sync সম্পূর্ণ হতে দিন (ইন্টারনেট লাগবে)।
4. `Build > Build Bundle(s) / APK(s) > Build APK(s)` নির্বাচন করুন।
5. সফল হলে APK পাবেন: `app/build/outputs/apk/debug/app-debug.apk`

বিকল্পভাবে প্রজেক্ট রুটে Android SDK/Gradle পরিবেশ প্রস্তুত থাকলে `gradle assembleDebug` চালাতে পারেন। Android-এর অফিসিয়াল গাইডে `assembleDebug` দিয়ে debug APK তৈরির নির্দেশনা আছে:
https://developer.android.com/build/building-cmdline

## সীমাবদ্ধতা

- এটি Android wrapper-এর সোর্স প্রজেক্ট, ইতোমধ্যে তৈরি APK ফাইল নয়।
- এই অ্যাপ ইন্টারনেট ছাড়া ড্যাশবোর্ড লোড করতে পারবে না।
- প্রকৃত OTC লাইভ মার্কেট ডেটা/API এখনো সংযুক্ত নয়; তাই এটি যাচাইকৃত ট্রেডিং সিগন্যাল তৈরি করে না।
- কোনো সিগন্যাল লাভের নিশ্চয়তা দেয় না।


## শুধু Android ফোন দিয়ে APK বানানো (GitHub Actions)

1. এই ZIP ফাইলটি ফোনে ডাউনলোড করে Extract করুন।
2. GitHub অ্যাকাউন্টে সাইন ইন করুন এবং নতুন **Public** repository তৈরি করুন, যেমন `eur-usd-otc-signals-android`।
3. Extract করা ফোল্ডারের ভেতরের সব ফাইল ও ফোল্ডার repository-তে আপলোড করুন। খেয়াল রাখবেন `.github/workflows/build-apk.yml` ফাইলটিও আপলোড হয়েছে।
4. Repository-র **Actions** ট্যাবে যান। প্রথমবার চাইলে **I understand my workflows, go ahead and enable them** চাপুন।
5. **Build Android APK** workflow খুলে **Run workflow** চাপুন (অথবা main branch-এ ফাইল আপলোড করলে স্বয়ংক্রিয়ভাবে শুরু হবে)।
6. Build শেষ হলে workflow run খুলুন; নিচের **Artifacts** অংশে `eur-usd-otc-signals-debug-apk` ডাউনলোড করুন।
7. ZIP artifact Extract করে `app-debug.apk` ফাইলটি খুলুন। Android চাইলে ব্রাউজার/ফাইল ম্যানেজার থেকে **Install unknown apps** অনুমতি দিন।

**নোট:** GitHub-এ ফাইল আপলোড করতে repository-র root-এ `settings.gradle`, `build.gradle`, `app/` এবং `.github/` থাকবে—এগুলোকে আরেকটি অতিরিক্ত ফোল্ডারের ভেতরে রেখে দেবেন না। GitHub Actions চালাতে ইন্টারনেট লাগবে।
