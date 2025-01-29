# Butlers
Home and office cleaning services
import React from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { useState } from "react";
import { motion } from "framer-motion";
import { DatePicker } from "@/components/ui/date-picker";

export default function CleaningServices() {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");
  const [message, setMessage] = useState("");
  const [selectedDate, setSelectedDate] = useState(null);

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Thank you, ${name}! We'll contact you soon. Your booking is set for ${selectedDate}.`);
  };

  return (
    <div className="min-h-screen p-6 bg-gray-50 text-gray-800">
      {/* Hero Section */}
      <motion.section
        className="text-center py-16 bg-green-500 text-white"
        initial={{ opacity: 0 }}
        animate={{ opacity: 1 }}
        transition={{ duration: 1 }}
      >
        <h1 className="text-4xl font-bold">Professional House Cleaning Services</h1>
        <p className="text-lg mt-4">We make your home sparkle with our top-quality services.</p>
        <Button className="mt-6 bg-white text-green-500 px-6 py-3 rounded-2xl font-semibold shadow-md">
          Book a Cleaning
        </Button>
      </motion.section>

      {/* Services Section */}
      <section className="py-12">
        <h2 className="text-3xl font-semibold text-center mb-8">Our Services</h2>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          {[
            { title: "Deep Cleaning", desc: "Perfect for a thorough top-to-bottom clean." },
            { title: "Move-In/Move-Out", desc: "Get your space ready for new occupants." },
            { title: "Recurring Cleaning", desc: "Weekly or monthly services to maintain cleanliness." },
          ].map((service, index) => (
            <Card key={index} className="shadow-lg hover:shadow-xl transition">
              <CardContent>
                <h3 className="text-xl font-bold mb-2">{service.title}</h3>
                <p>{service.desc}</p>
              </CardContent>
            </Card>
          ))}
        </div>
      </section>

      {/* Testimonials Section */}
      <section className="py-12 bg-gray-100">
        <h2 className="text-3xl font-semibold text-center mb-8">What Our Clients Say</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
          <Card className="shadow-md">
            <CardContent>
              <p>"The best cleaning service I've ever used! Highly recommend." - Jane D.</p>
            </CardContent>
          </Card>
          <Card className="shadow-md">
            <CardContent>
              <p>"They made my home look brand new. Absolutely amazing!" - Mark T.</p>
            </CardContent>
          </Card>
        </div>
      </section>

      {/* Contact Section */}
      <section className="py-12">
        <h2 className="text-3xl font-semibold text-center mb-8">Get In Touch</h2>
        <form onSubmit={handleSubmit} className="max-w-xl mx-auto space-y-4">
          <Input
            placeholder="Your Name"
            value={name}
            onChange={(e) => setName(e.target.value)}
            required
          />
          <Input
            type="email"
            placeholder="Your Email"
            value={email}
            onChange={(e) => setEmail(e.target.value)}
            required
          />
          <DatePicker
            selected={selectedDate}
            onChange={(date) => setSelectedDate(date)}
            placeholderText="Select a booking date"
            required
          />
          <Input
            placeholder="Your Message"
            value={message}
            onChange={(e) => setMessage(e.target.value)}
          />
          <Button type="submit" className="bg-green-500 w-full py-3 rounded-lg font-bold text-white">
            Submit
          </Button>
        </form>
      </section>

      {/* Contact Details */}
      <section className="py-12 bg-gray-200 text-center">
        <h2 className="text-3xl font-semibold mb-4">Contact Details</h2>
        <p className="text-lg">Phone: (123) 456-7890</p>
        <p className="text-lg">Email: info@cleaningservices.com</p>
        <p className="text-lg">Address: 123 Sparkle Street, Clean City, CL 45678</p>
      </section>
    </div>
  );
}
