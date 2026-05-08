import random
import time

target_ip = "192.168.1.10"
target_port = 80

half_open_connections = []


def generate_fake_ip():
   return f"192.168.{random.randint(0, 255)}.{random.randint(1, 254)}"


def syn_flood_simulation(packet_count=20):
   print("=== SYN Flood Simülasyonu Başlatıldı ===\n")

   for i in range(packet_count):
       fake_ip = generate_fake_ip()

       print(f"[+] SYN gönderildi -> {fake_ip}:{random.randint(1000, 5000)} → {target_ip}:{target_port}")

       half_open_connections.append(fake_ip)

       time.sleep(0.2)
       
print("\n=== Simülasyon Bitti ===")
   print(f"Toplam SYN paketi: {packet_count}")
   print(f"Half-open bağlantı sayısı: {len(half_open_connections)}")


def analyze_system():
   print("\n=== Sistem Analizi ===")

   if len(half_open_connections) > 15:
       print("⚠️ UYARI: Sistem aşırı yük altında!")
   else:
       print("✔️ Sistem normal çalışıyor")

   print("Bağlantı listesi:")
   for ip in half_open_connections[:5]:
       print(f"- {ip}")



syn_flood_simulation(20)
analyze_system()
