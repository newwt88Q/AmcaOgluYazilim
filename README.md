import Navbar from "@/components/navbar"
import Hero from "@/components/hero"
import Features from "@/components/features"
import Testimonials from "@/components/testimonials"
import ContactForm from "@/components/contact-form"
import Footer from "@/components/footer"

export default function Home() {
  return (
    <div className="min-h-screen flex flex-col">
      <Navbar />
      <main className="flex-grow">
        <Hero />
        <Features />
        <Testimonials />
        <ContactForm />
      </main>
      <Footer />
    </div>
  )
}

"use client"

import type React from "react"

import { useState } from "react"
import { Button } from "@/components/ui/button"
import { Input } from "@/components/ui/input"
import { Textarea } from "@/components/ui/textarea"
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "@/components/ui/card"

export default function ContactForm() {
  const [formData, setFormData] = useState({
    name: "",
    email: "",
    message: "",
  })

  const handleChange = (e: React.ChangeEvent<HTMLInputElement | HTMLTextAreaElement>) => {
    const { name, value } = e.target
    setFormData((prev) => ({ ...prev, [name]: value }))
  }

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault()
    // Form submission logic would go here
    alert("Mesajınız gönderildi! En kısa sürede size dönüş yapacağız.")
    setFormData({ name: "", email: "", message: "" })
  }

  return (
    <section id="contact" className="py-16 bg-gray-50 dark:bg-gray-900">
      <div className="container px-4 md:px-6">
        <div className="flex flex-col items-center justify-center space-y-4 text-center mb-12">
          <div className="space-y-2">
            <h2 className="text-3xl font-bold tracking-tighter sm:text-4xl md:text-5xl">İletişim</h2>
            <p className="max-w-[700px] text-gray-500 md:text-xl/relaxed lg:text-base/relaxed xl:text-xl/relaxed dark:text-gray-400">
              Sorularınız için bizimle iletişime geçin
            </p>
          </div>
        </div>
        <div className="mx-auto max-w-lg">
          <Card>
            <CardHeader>
              <CardTitle>Bize Ulaşın</CardTitle>
              <CardDescription>Formu doldurarak mesajınızı iletebilirsiniz.</CardDescription>
            </CardHeader>
            <CardContent>
              <form onSubmit={handleSubmit} className="space-y-4">
                <div className="space-y-2">
                  <label
                    htmlFor="name"
                    className="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
                  >
                    İsim Soyisim
                  </label>
                  <Input
                    id="name"
                    name="name"
                    value={formData.name}
                    onChange={handleChange}
                    placeholder="İsim Soyisim"
                    required
                  />
                </div>
                <div className="space-y-2">
                  <label
                    htmlFor="email"
                    className="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
                  >
                    E-posta
                  </label>
                  <Input
                    id="email"
                    name="email"
                    type="email"
                    value={formData.email}
                    onChange={handleChange}
                    placeholder="ornek@email.com"
                    required
                  />
                </div>
                <div className="space-y-2">
                  <label
                    htmlFor="message"
                    className="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
                  >
                    Mesajınız
                  </label>
                  <Textarea
                    id="message"
                    name="message"
                    value={formData.message}
                    onChange={handleChange}
                    placeholder="Mesajınızı buraya yazın..."
                    className="min-h-[120px]"
                    required
                  />
                </div>
                <Button type="submit" className="w-full">
                  Gönder
                </Button>
              </form>
            </CardContent>
          </Card>
        </div>
      </div>
    </section>
  )
}
import { CheckCircle, Zap, Shield, Globe } from "lucide-react"
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "@/components/ui/card"

export default function Features() {
  const features = [
    {
      icon: <Zap className="h-10 w-10 text-primary" />,
      title: "Hızlı Performans",
      description: "Yüksek hızlı sunucular ve optimize edilmiş kodlar ile siteniz saniyeler içinde yüklenir.",
    },
    {
      icon: <Shield className="h-10 w-10 text-primary" />,
      title: "Güvenli Altyapı",
      description: "SSL sertifikası ve güncel güvenlik önlemleri ile verileriniz her zaman güvende.",
    },
    {
      icon: <Globe className="h-10 w-10 text-primary" />,
      title: "Mobil Uyumlu",
      description: "Tüm cihazlarda mükemmel görünen responsive tasarım ile her yerde erişilebilirlik.",
    },
    {
      icon: <CheckCircle className="h-10 w-10 text-primary" />,
      title: "SEO Dostu",
      description: "Arama motorlarında üst sıralarda yer almanız için optimize edilmiş yapı.",
    },
  ]

  return (
    <section id="features" className="py-16 bg-gray-50 dark:bg-gray-900">
      <div className="container px-4 md:px-6">
        <div className="flex flex-col items-center justify-center space-y-4 text-center mb-12">
          <div className="space-y-2">
            <h2 className="text-3xl font-bold tracking-tighter sm:text-4xl md:text-5xl">Özellikler</h2>
            <p className="max-w-[700px] text-gray-500 md:text-xl/relaxed lg:text-base/relaxed xl:text-xl/relaxed dark:text-gray-400">
              Web sitenizi öne çıkaran özelliklerimiz
            </p>
          </div>
        </div>
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
          {features.map((feature, index) => (
            <Card key={index} className="border-none shadow-md">
              <CardHeader className="pb-2">
                <div className="mb-2">{feature.icon}</div>
                <CardTitle>{feature.title}</CardTitle>
              </CardHeader>
              <CardContent>
                <CardDescription className="text-base">{feature.description}</CardDescription>
              </CardContent>
            </Card>
          ))}
        </div>
      </div>
    </section>
  )
}
import Link from "next/link"
import { Facebook, Twitter, Instagram, Linkedin } from "lucide-react"

export default function Footer() {
  return (
    <footer className="border-t bg-background">
      <div className="container px-4 md:px-6 py-8">
        <div className="grid grid-cols-1 md:grid-cols-4 gap-8">
          <div className="space-y-4">
            <h3 className="text-lg font-bold">WebSite</h3>
            <p className="text-sm text-gray-500 dark:text-gray-400">Modern ve profesyonel web çözümleri sunuyoruz.</p>
            <div className="flex space-x-4">
              <Link href="#" className="text-gray-500 hover:text-primary">
                <Facebook className="h-5 w-5" />
                <span className="sr-only">Facebook</span>
              </Link>
              <Link href="#" className="text-gray-500 hover:text-primary">
                <Twitter className="h-5 w-5" />
                <span className="sr-only">Twitter</span>
              </Link>
              <Link href="#" className="text-gray-500 hover:text-primary">
                <Instagram className="h-5 w-5" />
                <span className="sr-only">Instagram</span>
              </Link>
              <Link href="#" className="text-gray-500 hover:text-primary">
                <Linkedin className="h-5 w-5" />
                <span className="sr-only">LinkedIn</span>
              </Link>
            </div>
          </div>
          <div>
            <h3 className="text-lg font-bold mb-4">Hızlı Bağlantılar</h3>
            <ul className="space-y-2 text-sm">
              <li>
                <Link href="#" className="text-gray-500 hover:text-primary">
                  Ana Sayfa
                </Link>
              </li>
              <li>
                <Link href="#features" className="text-gray-500 hover:text-primary">
                  Özellikler
                </Link>
              </li>
              <li>
                <Link href="#testimonials" className="text-gray-500 hover:text-primary">
                  Referanslar
                </Link>
              </li>
              <li>
                <Link href="#contact" className="text-gray-500 hover:text-primary">
                  İletişim
                </Link>
              </li>
            </ul>
          </div>
          <div>
            <h3 className="text-lg font-bold mb-4">Hizmetlerimiz</h3>
            <ul className="space-y-2 text-sm">
              <li>
                <Link href="#" className="text-gray-500 hover:text-primary">
                  Web Tasarım
                </Link>
              </li>
              <li>
                <Link href="#" className="text-gray-500 hover:text-primary">
                  E-Ticaret
                </Link>
              </li>
              <li>
                <Link href="#" className="text-gray-500 hover:text-primary">
                  SEO
                </Link>
              </li>
              <li>
                <Link href="#" className="text-gray-500 hover:text-primary">
                  Dijital Pazarlama
                </Link>
              </li>
            </ul>
          </div>
          <div>
            <h3 className="text-lg font-bold mb-4">İletişim</h3>
            <address className="not-italic text-sm text-gray-500 space-y-2">
              <p>İstanbul, Türkiye</p>
              <p>info@website.com</p>
              <p>+90 212 123 45 67</p>
            </address>
          </div>
        </div>
        <div className="mt-8 border-t pt-8 text-center text-sm text-gray-500">
          <p>&copy; {new Date().getFullYear()} WebSite. Tüm hakları saklıdır.</p>
        </div>
      </div>
    </footer>
  )
}
import Image from "next/image"
import { Button } from "@/components/ui/button"

export default function Hero() {
  return (
    <section className="py-20 md:py-28">
      <div className="container px-4 md:px-6">
        <div className="grid gap-6 lg:grid-cols-2 lg:gap-12 items-center">
          <div className="flex flex-col justify-center space-y-4">
            <div className="space-y-2">
              <h1 className="text-3xl font-bold tracking-tighter sm:text-5xl xl:text-6xl/none">Modern Web Çözümleri</h1>
              <p className="max-w-[600px] text-gray-500 md:text-xl dark:text-gray-400">
                İşletmeniz için profesyonel, hızlı ve kullanıcı dostu web siteleri. Müşterilerinize en iyi dijital
                deneyimi sunun.
              </p>
            </div>
            <div className="flex flex-col gap-2 min-[400px]:flex-row">
              <Button size="lg" className="px-8">
                Ücretsiz Başlayın
              </Button>
              <Button size="lg" variant="outline" className="px-8">
                Demo İzleyin
              </Button>
            </div>
          </div>
          <div className="flex items-center justify-center">
            <div className="relative w-full max-w-[500px] aspect-video overflow-hidden rounded-xl">
              <Image
                src="/placeholder.svg?height=500&width=800"
                alt="Web site görseli"
                width={800}
                height={500}
                className="object-cover"
                priority
              />
            </div>
          </div>
        </div>
      </div>
    </section>
  )
}
"use client"

import { useState } from "react"
import Link from "next/link"
import { Menu, X } from "lucide-react"
import { Button } from "@/components/ui/button"

export default function Navbar() {
  const [isMenuOpen, setIsMenuOpen] = useState(false)

  return (
    <header className="sticky top-0 z-50 w-full border-b bg-background/95 backdrop-blur supports-[backdrop-filter]:bg-background/60">
      <div className="container flex h-16 items-center justify-between">
        <div className="flex items-center gap-2">
          <Link href="/" className="font-bold text-xl">
            WebSite
          </Link>
        </div>

        {/* Desktop Navigation */}
        <nav className="hidden md:flex items-center gap-6">
          <Link href="#features" className="text-sm font-medium transition-colors hover:text-primary">
            Özellikler
          </Link>
          <Link href="#testimonials" className="text-sm font-medium transition-colors hover:text-primary">
            Referanslar
          </Link>
          <Link href="#contact" className="text-sm font-medium transition-colors hover:text-primary">
            İletişim
          </Link>
          <Button>Başlayın</Button>
        </nav>

        {/* Mobile Menu Button */}
        <button
          className="md:hidden"
          onClick={() => setIsMenuOpen(!isMenuOpen)}
          aria-label={isMenuOpen ? "Menüyü kapat" : "Menüyü aç"}
        >
          {isMenuOpen ? <X className="h-6 w-6" /> : <Menu className="h-6 w-6" />}
        </button>
      </div>

      {/* Mobile Navigation */}
      {isMenuOpen && (
        <div className="md:hidden container py-4 border-t">
          <nav className="flex flex-col space-y-4">
            <Link
              href="#features"
              className="text-sm font-medium transition-colors hover:text-primary"
              onClick={() => setIsMenuOpen(false)}
            >
              Özellikler
            </Link>
            <Link
              href="#testimonials"
              className="text-sm font-medium transition-colors hover:text-primary"
              onClick={() => setIsMenuOpen(false)}
            >
              Referanslar
            </Link>
            <Link
              href="#contact"
              className="text-sm font-medium transition-colors hover:text-primary"
              onClick={() => setIsMenuOpen(false)}
            >
              İletişim
            </Link>
            <Button className="w-full">Başlayın</Button>
          </nav>
        </div>
      )}
    </header>
  )
}
import Image from "next/image"
import { Card, CardContent, CardFooter } from "@/components/ui/card"

export default function Testimonials() {
  const testimonials = [
    {
      quote: "Bu web sitesi sayesinde online satışlarımız %40 arttı. Kullanımı çok kolay ve müşterilerimiz çok memnun.",
      author: "Ahmet Yılmaz",
      role: "ABC Şirketi CEO",
      avatar: "/placeholder.svg?height=100&width=100",
    },
    {
      quote: "Profesyonel tasarım ve hızlı destek için teşekkürler. Tam ihtiyacımız olan çözümü sundunuz.",
      author: "Ayşe Kaya",
      role: "XYZ Mağazaları Müdürü",
      avatar: "/placeholder.svg?height=100&width=100",
    },
    {
      quote:
        "Mobil uyumlu tasarım sayesinde müşterilerimiz her yerden sitemize erişebiliyor. Harika bir iş çıkardınız.",
      author: "Mehmet Demir",
      role: "123 Teknoloji Kurucusu",
      avatar: "/placeholder.svg?height=100&width=100",
    },
  ]

  return (
    <section id="testimonials" className="py-16">
      <div className="container px-4 md:px-6">
        <div className="flex flex-col items-center justify-center space-y-4 text-center mb-12">
          <div className="space-y-2">
            <h2 className="text-3xl font-bold tracking-tighter sm:text-4xl md:text-5xl">Müşteri Yorumları</h2>
            <p className="max-w-[700px] text-gray-500 md:text-xl/relaxed lg:text-base/relaxed xl:text-xl/relaxed dark:text-gray-400">
              Müşterilerimizin bizimle çalışma deneyimleri
            </p>
          </div>
        </div>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          {testimonials.map((testimonial, index) => (
            <Card key={index} className="text-center">
              <CardContent className="pt-6">
                <div className="mx-auto mb-4 flex h-16 w-16 items-center justify-center overflow-hidden rounded-full">
                  <Image
                    src={testimonial.avatar || "/placeholder.svg"}
                    alt={testimonial.author}
                    width={100}
                    height={100}
                    className="object-cover"
                  />
                </div>
                <blockquote className="border-l-4 border-primary pl-4 italic">"{testimonial.quote}"</blockquote>
              </CardContent>
              <CardFooter className="flex flex-col">
                <p className="font-semibold">{testimonial.author}</p>
                <p className="text-sm text-gray-500">{testimonial.role}</p>
              </CardFooter>
            </Card>
          ))}
        </div>
      </div>
    </section>
  )
}
