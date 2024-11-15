'use client'

import { useState, useEffect, useRef } from 'react'
import { Button } from "@/components/ui/button"
import { Input } from "@/components/ui/input"
import { ChevronLeft, ChevronRight, Gift, Building, Calendar, Package, Star, Heart, ThumbsUp, Instagram, Twitter, Facebook, Moon, Sun } from 'lucide-react'
import Image from 'next/image'
import { motion, useScroll, useTransform } from 'framer-motion'

export default function UltraEnhancedGiftWebsite() {
  const [currentTestimonialSet, setCurrentTestimonialSet] = useState(0)
  const [isLightMode, setIsLightMode] = useState(true)
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 })
  const backgroundRef = useRef(null)

  const { scrollYProgress } = useScroll()
  const backgroundY = useTransform(scrollYProgress, [0, 1], ['0%', '50%'])

  const services = [
    {
      title: "هدایا شخصی سازی",
      description: "با جواب دادن به چند سوال ساده، بهترین ایده هدیه رو برای دوستت پیدا کن. بقیه کارهاش رو به ما بسپار. ما مهر و محبت رو به در خونه‌ات می‌رسونیم",
      icon: <Gift className="w-16 h-16" />,
      link: "https://survey.porsline.ir/s/yIYJprF4"
    },
    {
      title: "هدیه شرکتی",
      description: "هدیه‌های شرکتی ما به شما کمک می‌کنن تا ارتباطات کاری‌تون رو با شادی و خلاقیت تقویت کنید. بسته‌بندی اختصاصی با لوگوی شرکت شما",
      icon: <Building className="w-16 h-16" />,
      link: "https://survey.porsline.ir/s/MYOIPu61"
    },
    {
      title: "هدیه رویدادی",
      description: "ما تو کادوچی، پک های مناسب برای هر رویداد یا ایونت رو با عشق آماده می‌کنیم و با بسته‌بندی حرفه‌ای تحویلتون می‌دیم. هدیه‌ای برای خلق شادی و خاطره",
      icon: <Calendar className="w-16 h-16" />,
      link: "https://survey.porsline.ir/s/za0f4eOO"
    },
    {
      title: "بسته‌بندی با عشق",
      description: "تو کادوچی، ما شادی رو حتی توی بسته‌بندی هدیه‌هاتون هم می‌ریزیم. کاغذ کادوی دلخواهتون رو انتخاب کنید و با یه دست‌نوشته یا پیام صوتی، هدیه رو خاص‌تر کنی",
      icon: <Package className="w-16 h-16" />,
      link: "#"
    }
  ]

  const teamMembers = [
    { name: "کمیل افخمی", image: "/placeholder.svg?height=200&width=200" },
    { name: "امیرحسین عابدی", image: "/placeholder.svg?height=200&width=200" },
    { name: "فاطمه بندهی", image: "/placeholder.svg?height=200&width=200" }
  ]

  const testimonials = [
    {
      text: "من بسته رو دریافت کردم، بی‌نهایت برام عزیز بود و مرسی ازتون 🤍 به قاب گوشیم میومد، رنگشم رنگ مورد علاقم بود و حسابی ذوق کردم.",
      icon: <Star className="w-8 h-8 text-yellow-400" />
    },
    {
      text: "!!انتخابتون عالیه واقعا من مدت ها بود میخواستم اون گردنبند پرو بخرم و نمیشد عاشق پروانه هم هستم دیگه:)",
      icon: <Heart className="w-8 h-8 text-red-500" />
    },
    {
      text: "خیلی جالب بود. کاور دوست‌داشتنی و متن دست‌نوشته حس خوبی به من داد. به نوعی بسته شخصی سازی شده بود و هدیه با شناخت علاقه‌هایم انتخاب شده بود",
      icon: <ThumbsUp className="w-8 h-8 text-blue-500" />
    },
    {
      text: "کادو چی عزیز💘 شما رسالتتون انتقال حس خوب به آدماست خیلی خوشحال شدم بابت هدیه‌ها",
      icon: <Star className="w-8 h-8 text-yellow-400" />
    },
    {
      text: "خود هدیه که نویسنده‌ش عالیه ✨و نمی‌تونم صبر کنم که بخونمش و بسته بندی هم بیاین از این نگذریم که رنگ مورد علاقمه و خیلیییی دوس داشتنی بود",
      icon: <Heart className="w-8 h-8 text-red-500" />
    },
    {
      text: "با خوندن چیزی که برام نوشته بودن حس غیر قابل توصیفی داشتم که نمیشه گفت فقط خوشحالیه",
      icon: <ThumbsUp className="w-8 h-8 text-blue-500" />
    }
  ]

  const giftExamples = [
    { image: "/placeholder.svg?height=300&width=300" },
    { image: "/placeholder.svg?height=300&width=300" },
    { image: "/placeholder.svg?height=300&width=300" },
    { image: "/placeholder.svg?height=300&width=300" },
    { image: "/placeholder.svg?height=300&width=300" },
    { image: "/placeholder.svg?height=300&width=300" },
  ]

  const nextTestimonial = () => {
    setCurrentTestimonialSet((prev) => (prev + 1) % (testimonials.length / 3))
  }

  const prevTestimonial = () => {
    setCurrentTestimonialSet((prev) => (prev - 1 + testimonials.length / 3) % (testimonials.length / 3))
  }

  useEffect(() => {
    const testimonialElements = document.querySelectorAll('.testimonial-item');
    testimonialElements.forEach((el, index) => {
      setTimeout(() => {
        (el as HTMLElement).style.opacity = '1';
        (el as HTMLElement).style.transform = 'translateY(0) rotate(0)';
      }, index * 200);
    });
  }, [currentTestimonialSet]);

  const toggleTheme = () => {
    setIsLightMode(!isLightMode);
    document.documentElement.classList.toggle('dark');
  }

  useEffect(() => {
    const handleMouseMove = (e: MouseEvent) => {
      setMousePosition({ x: e.clientX, y: e.clientY })
    }

    window.addEventListener('mousemove', handleMouseMove)

    return () => {
      window.removeEventListener('mousemove', handleMouseMove)
    }
  }, [])

  return (
    <div className={`min-h-screen font-['Dana'] transition-colors duration-300 ${isLightMode ? 'bg-gradient-to-br from-pink-100 via-white to-blue-100' : 'dark bg-gradient-to-br from-gray-900 via-purple-900 to-violet-900'}`}>
      <div 
        ref={backgroundRef}
        className="fixed inset-0 pointer-events-none z-0"
        style={{
          backgroundImage: `url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%239C92AC' fill-opacity='0.1'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E")`,
          backgroundAttachment: 'fixed',
          transform: `translateY(${backgroundY}px)`,
        }}
      ></div>
      <div 
        className="fixed inset-0 pointer-events-none z-10"
        style={{
          background: `radial-gradient(circle at ${mousePosition.x}px ${mousePosition.y}px, rgba(255,255,255,0.1) 0%, rgba(255,255,255,0) 50%)`,
        }}
      ></div>

      <header className="bg-gradient-to-r from-[#3b3d98] to-[#FF69B4] text-white p-4 shadow-md sticky top-0 z-50">
        <div className="container mx-auto flex justify-between items-center">
          <a href="#" className="text-white hover:text-gray-200 transition duration-300 text-2xl font-bold">کادوچی</a>
          <nav className="space-x-4">
            <a href="#services" className="text-white hover:text-gray-200 transition duration-300">خدمات</a>
            <a href="#team" className="text-white hover:text-gray-200 transition duration-300">تیم ما</a>
            <a href="#testimonials" className="text-white hover:text-gray-200 transition duration-300">نظرات</a>
            <a href="#contact" className="text-white hover:text-gray-200 transition duration-300">تماس</a>
          </nav>
          <button onClick={toggleTheme} className="p-2 rounded-full bg-white text-[#3b3d98] hover:bg-gray-200 transition duration-300">
            {isLightMode ? <Moon className="w-6 h-6" /> : <Sun className="w-6 h-6" />}
          </button>
        </div>
      </header>

      <main className="relative z-20">
        <section className="py-20 text-center relative overflow-hidden">
          <motion.div 
            initial={{ opacity: 0, y: 50 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.8 }}
            className="container mx-auto px-4 relative z-10"
          >
            <h1 className="text-5xl md:text-7xl font-bold mb-6 bg-clip-text text-transparent bg-gradient-to-r from-[#3b3d98] to-[#FF69B4]">
              نمی‌دونید چی هدیه بدین؟
            </h1>
            <p className="text-2xl md:text-3xl mb-8 text-gray-700 dark:text-gray-300">
              !ما راه‌حلش رو داریم
            </p>
            <Button 
              className="bg-gradient-to-r from-[#3b3d98] to-[#FF69B4] hover:from-[#FF69B4] hover:to-[#3b3d98] text-white px-8 py-3 text-lg rounded-full transition duration-300 ease-in-out transform hover:scale-105 shadow-lg animate-pulse"
              onClick={() => window.location.href = 'https://survey.porsline.ir/s/yIYJprF4'}
            >
              !بزن بریم
            </Button>
          </motion.div>
          <div className="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-full h-full z-0">
            <div className="absolute top-0 left-0 w-full h-full bg-gradient-to-b from-transparent to-white dark:to-gray-900 opacity-50"></div>
            <svg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg" className="w-full h-full">
              <path fill={isLightMode ? "#FF69B4" : "#3b3d98"} d="M44.7,-76.4C58.8,-69.2,71.8,-59.1,79.6,-45.8C87.4,-32.5,90,-16.3,88.5,-1.5C87,13.3,81.4,26.7,73.6,38.4C65.8,50.1,55.9,60.1,43.9,66.5C31.9,72.9,16,75.7,0.7,74.6C-14.6,73.5,-29.2,68.5,-41.9,61C-54.6,53.5,-65.4,43.4,-71.8,30.8C-78.2,18.2,-80.1,3,-78.1,-11.4C-76.1,-25.8,-70.2,-39.5,-60.4,-49.4C-50.6,-59.3,-36.9,-65.5,-23.7,-73.1C-10.5,-80.7,2.2,-89.7,15.8,-89.7C29.5,-89.7,58.9,-80.7,44.7,-76.4Z" transform="translate(100 100)" />
            </svg>
          </div>
        </section>

        <section id="services" className="py-20 bg-white dark:bg-gray-800 transition-colors duration-300">
          <div className="container mx-auto px-4">
            <h2 className="text-4xl font-bold text-center mb-16 bg-clip-text text-transparent bg-gradient-to-r from-[#3b3d98] to-[#FF69B4]">خدمات ما</h2>
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
              {services.map((service, index) => (
                <motion.div
                  key={index}
                  initial={{ opacity: 0, y: 50 }}
                  animate={{ opacity: 1, y: 0 }}
                  transition={{ duration: 0.5, delay: index * 0.1 }}
                >
                  <a href={service.link} className="block group">
                    <div className="bg-gradient-to-br from-white to-pink-100 dark:from-gray-800 dark:to-purple-900 rounded-lg shadow-lg p-6 transition duration-300 ease-in-out transform hover:-translate-y-2 hover:shadow-xl">
                      <div className="flex justify-center mb-6 group-hover:scale-110 transition-transform duration-300">
                        <div className="text-[#3b3d98] dark:text-[#FF69B4]">{service.icon}</div>
                      </div>
                      <h3 className="text-xl font-semibold mb-4 text-center text-[#3b3d98] dark:text-[#FF69B4]">{service.title}</h3>
                      <p className="text-center text-gray-600 dark:text-gray-300">{service.description}</p>
                    </div>
                  </a>
                </motion.div>
              ))}
            </div>
          </div>
        </section>

        <section id="team" className="py-20 bg-gradient-to-r from-pink-100 to-blue-100 dark:from-gray-900 dark:to-purple-900 transition-colors duration-300">
          <div className="container mx-auto px-4">
            <h2 className="text-4xl font-bold text-center mb-16 bg-clip-text text-transparent bg-gradient-to-r from-[#3b3d98] to-[#FF69B4]">تیم ما</h2>
            <div className="flex flex-wrap justify-center gap-12">
              {teamMembers.map((member, index) => (
                <motion.div
                  key={index}
                  initial={{ opacity: 0, scale: 0.5 }}
                  animate={{ opacity: 1, scale: 1 }}
                  transition={{ duration: 0.5, delay: index * 0.2 }}
                  className="text-center group"
                >
                  <div className="relative w-48 h-48 mx-auto mb-6 overflow-hidden rounded-full shadow-lg border-4 border-[#7678b7] group-hover:border-[#3b3d98] transition-colors duration-300">
                    <Image src={member.image} alt={member.name} width={200} height={200} className="w-full h-full object-cover transition-transform duration-300 group-hover:scale-110" />
                  </div>
                  <h3 className="text-2xl font-semibold text-[#3b3d98] dark:text-[#FF69B4]">{member.name}</h3>
                </motion.div>
              ))}
            </div>
          </div>
        </section>

        <section id="testimonials" className="py-20 bg-white dark:bg-gray-800 relative overflow-hidden transition-colors duration-300">
          <div className="container mx-auto px-4 relative z-10">
            <h2 className="text-4xl font-bold text-center mb-16 bg-clip-text text-transparent bg-gradient-to-r from-[#3b3d98] to-[#FF69B4]">نظرات مشتریان</h2>
            <div className="relative max-w-5xl mx-auto">
              <div className="grid grid-cols-1 md:grid-cols-3 gap-8 mb-12">
                {testimonials.slice(currentTestimonialSet * 3, (currentTestimonialSet + 1) * 3).map((testimonial, index) => (
                  <motion.div 
                    key={index}
                    initial={{ opacity: 0, y: 50, rotate: -5 }}
                    animate={{ opacity: 1, y: 0, rotate: 0 }}
                    transition={{ duration: 0.5, delay: index * 0.1 }}
                    className="bg-gradient-to-br from-white to-pink-100 dark:from-gray-800 dark:to-purple-900 p-6 rounded-lg shadow-lg flex flex-col items-center justify-between h-64"
                  >
                    <div className="mb-4">{testimonial.icon}</div>
                    <p className="text-gray-700 dark:text-gray-300 text-sm text-center flex-grow">{testimonial.text}</p>
                    <div className="w-12 h-1 bg-gradient-to-r from-[#3b3d98] to-[#FF69B4] mt-4"></div>
                  </motion.div>
                ))}
              </div>
              <div className="flex justify-center gap-4 mt-8">
                <Button onClick={prevTestimonial} variant="outline" size="icon" className="bg-[#3b3d98] text-white hover:bg-[#FF69B4] transition-colors duration-300">
                  <ChevronRight className="h-6 w-6" />
                </Button>
                <Button onClick={nextTestimonial} variant="outline" size="icon" className="bg-[#3b3d98] text-white hover:bg-[#FF69B4] transition-colors duration-300">
                  <ChevronLeft className="h-6 w-6" />
                </Button>
              </div>
            </div>
          </div>
          <div className="absolute top-0 left-0 w-full h-full">
            <div className="absolute top-10 left-10 w-20 h-20 bg-[#FF69B4] rounded-full opacity-20 animate-pulse"></div>
            <div className="absolute bottom-10 right-10 w-32 h-32 bg-[#3b3d98] rounded-full opacity-20 animate-pulse"></div>
            <div className="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-40 h-40 bg-[#7678b7] rounded-full opacity-10 animate-pulse"></div>
          </div>
        </section>

        <section className="py-20 bg-gradient-to-r from-pink-100 to-blue-100 dark:from-gray-900 dark:to-purple-900 transition-colors duration-300">
          <div className="container mx-auto px-4">
            <h2 className="text-4xl font-bold text-center mb-16 bg-clip-text text-transparent bg-gradient-to-r from-[#3b3d98] to-[#FF69B4]">نمونه هدیه‌ها</h2>
            <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
              {giftExamples.map((gift, index) => (
                <motion.div
                  key={index}
                  initial={{ opacity: 0, scale: 0.8 }}
                  animate={{ opacity: 1, scale: 1 }}
                  transition={{ duration: 0.5, delay: index * 0.1 }}
                  className="bg-white dark:bg-gray-800 rounded-lg shadow-lg overflow-hidden group hover:shadow-xl transition-shadow duration-300"
                >
                  <div className="relative h-80 overflow-hidden">
                    <Image src={gift.image} alt="Gift example" layout="fill" objectFit="cover" className="transition-transform duration-300 group-hover:scale-110" />
                  </div>
                </motion.div>
              ))}
            </div>
          </div>
        </section>

        <section id="contact" className="py-20 bg-white dark:bg-gray-800 transition-colors duration-300">
          <div className="container mx-auto px-4">
            <h2 className="text-4xl font-bold text-center mb-16 bg-clip-text text-transparent bg-gradient-to-r from-[#3b3d98] to-[#FF69B4]">تماس با ما</h2>
            <div className="max-w-md mx-auto">
              <form className="space-y-4">
                <Input type="text" placeholder="نام" className="w-full bg-gray-100 dark:bg-gray-700 border-none" />
                <Input type="email" placeholder="ایمیل" className="w-full bg-gray-100 dark:bg-gray-700 border-none" />
                <textarea className="w-full h-32 p-2 bg-gray-100 dark:bg-gray-700 rounded-md resize-none focus:outline-none focus:ring-2 focus:ring-[#3b3d98]" placeholder="پیام شما"></textarea>
                <Button className="w-full bg-gradient-to-r from-[#3b3d98] to-[#FF69B4] hover:from-[#FF69B4] hover:to-[#3b3d98] text-white transition-colors duration-300">ارسال پیام</Button>
              </form>
            </div>
          </div>
        </section>
      </main>

      <footer className="bg-gradient-to-r from-[#3b3d98] to-[#FF69B4] text-white py-12">
        <div className="container mx-auto px-4">
          <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div>
              <h3 className="text-2xl font-bold mb-4">درباره ما</h3>
              <p className="mb-4">کادوچی توسط یک تیم صمیمی از سه نفر که از نقاط مختلف ایران گرد هم اومدن، اداره می‌شه. ما اینجاییم تا به شما کمک کنیم محبت خودتون رو به شیوه‌ای متفاوت نشون بدید!</p>
              <p>برای سفارش هدیه و دریافت اطلاعات بیشتر، لطفاً از طریق راه‌های ارتباطی با ما در تماس باشید.</p>
            </div>
            <div>
              <h3 className="text-2xl font-bold mb-4">خدمات</h3>
              <ul className="space-y-2">
                <li>پیام ناشناس</li>
                <li>شخصی سازی بسته بندی</li>
                <li>هدایای سازمانی</li>
              </ul>
            </div>
            <div>
              <h3 className="text-2xl font-bold mb-4">ارتباط با ما</h3>
              <p>تهران ، کارخانه نوآوری آزادی ، سوله دیجی نکست</p>
              <p>09146127298</p>
              <p>kadochi2024@gmail.com</p>
              <div className="flex space-x-4 mt-4">
                <a href="#" className="text-white hover:text-pink-200 transition-colors duration-300">
                  <Instagram className="w-6 h-6" />
                </a>
                <a href="#" className="text-white hover:text-pink-200 transition-colors duration-300">
                  <Twitter className="w-6 h-6" />
                </a>
                <a href="#" className="text-white hover:text-pink-200 transition-colors duration-300">
                  <Facebook className="w-6 h-6" />
                </a>
              </div>
            </div>
          </div>
        </div>
      </footer>
    </div>
  )
}
