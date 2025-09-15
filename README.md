# Speech To Text Sample

Bu proje, ses dosyalarını veya mikrofondan alınan sesleri OpenAI Whisper modeli ile metne çeviren örnek bir uygulamadır.

## İçerik

- `audio.wav`: Örnek ses dosyası.
- `kayit.wav`: Mikrofondan kaydedilen ses dosyası.
- [`STT.ipynb`](STT.ipynb): Jupyter Notebook formatında, ses dosyasını veya mikrofondan alınan sesi metne çeviren kod örnekleri.

## Kullanım

1. **Google Colab'da Çalıştırma (Tavsiye Edilen Yöntem)**

   - [Google Colab](https://colab.research.google.com/) üzerinde çalışmak için, üst menüden `Runtime` → `Change runtime type` seçeneğine tıklayın ve `Hardware accelerator` olarak **GPU (T4)** seçin.
   - Notebook'u yükleyin ve hücreleri sırayla çalıştırın.
   - GPU ile daha hızlı ve verimli çalışır. (T4 GPU kullanılarak geliştirilmiştir.)

2. **Gerekli Kütüphaneleri Kurun:**
   Notebook içinde aşağıdaki komutları çalıştırın:
   ```python
   !apt-get update -qq && apt-get install -y -qq ffmpeg
   !pip install -q -U openai-whisper soundfile
   ```

3. **Modeli Yükleyin ve Ses Dosyasını Metne Çevirin:**
   ```python
   import whisper
   import torch

   device = "cuda" if torch.cuda.is_available() else "cpu"
   model = whisper.load_model("base", device=device)
   result = model.transcribe("audio.wav")
   print(result["text"])
   ```

4. **Mikrofondan Kayıt Alıp Metne Çevirin:**
   Notebook'taki ilgili hücreleri çalıştırarak mikrofondan kayıt alabilir ve kaydı metne çevirebilirsiniz.

## Notlar

- GPU ile daha hızlı sonuç almak için Colab veya benzeri bir ortamda çalışabilirsiniz.
- Farklı model boyutları (`tiny`, `base`, `small`, `medium`, `large`) kullanılabilir. Model boyutu arttıkça doğruluk artar, hız azalır.
- Notebook'ta örnek kodlar ve açıklamalar Türkçe olarak yer almaktadır.

## Kaynaklar

- [OpenAI Whisper Modeli](https://huggingface.co/openai/whisper-base)
- [Whisper Github](https://github.com/openai/whisper)
