# netflix-clone
import { useState } from 'react'
import { ChevronLeft, ChevronRight, Play, Info } from 'lucide-react'
import { Button } from "@/components/ui/button"

export default function Component() {
  const [heroIndex, setHeroIndex] = useState(0)
  const heroContent = [
    {
      title: "Stranger Things",
      description: "When a young boy vanishes, a small town uncovers a mystery involving secret experiments, terrifying supernatural forces, and one strange little girl.",
      image: "/placeholder.svg?height=600&width=1200"
    },
    {
      title: "The Crown",
      description: "This drama follows the political rivalries and romance of Queen Elizabeth II's reign and the events that shaped the second half of the 20th century.",
      image: "/placeholder.svg?height=600&width=1200"
    },
    {
      title: "Bridgerton",
      description: "The eight close-knit siblings of the Bridgerton family look for love and happiness in London high society.",
      image: "/placeholder.svg?height=600&width=1200"
    }
  ]

  const categories = [
    { name: "Trending Now", items: [1, 2, 3, 4, 5, 6] },
    { name: "New Releases", items: [1, 2, 3, 4, 5, 6] },
    { name: "Top Picks for You", items: [1, 2, 3, 4, 5, 6] },
  ]

  return (
    <div className="min-h-screen bg-black text-white">
      {/* Hero Section */}
      <div className="relative h-[56.25vw] max-h-[80vh]">
        <img
          src={heroContent[heroIndex].image}
          alt={heroContent[heroIndex].title}
          className="w-full h-full object-cover"
        />
        <div className="absolute inset-0 bg-gradient-to-t from-black to-transparent" />
        <div className="absolute bottom-0 left-0 p-8 w-full md:w-1/2">
          <h1 className="text-4xl md:text-6xl font-bold mb-4">{heroContent[heroIndex].title}</h1>
          <p className="text-lg mb-6">{heroContent[heroIndex].description}</p>
          <div className="flex space-x-4">
            <Button className="bg-white text-black hover:bg-gray-200">
              <Play className="mr-2 h-4 w-4" /> Play
            </Button>
            <Button variant="outline">
              <Info className="mr-2 h-4 w-4" /> More Info
            </Button>
          </div>
        </div>
        <div className="absolute top-1/2 left-4 transform -translate-y-1/2">
          <Button
            variant="outline"
            size="icon"
            className="rounded-full"
            onClick={() => setHeroIndex((prev) => (prev === 0 ? heroContent.length - 1 : prev - 1))}
          >
            <ChevronLeft className="h-4 w-4" />
          </Button>
        </div>
        <div className="absolute top-1/2 right-4 transform -translate-y-1/2">
          <Button
            variant="outline"
            size="icon"
            className="rounded-full"
            onClick={() => setHeroIndex((prev) => (prev === heroContent.length - 1 ? 0 : prev + 1))}
          >
            <ChevronRight className="h-4 w-4" />
          </Button>
        </div>
      </div>

      {/* Categories */}
      <div className="px-8 py-12 space-y-12">
        {categories.map((category) => (
          <div key={category.name}>
            <h2 className="text-2xl font-semibold mb-4">{category.name}</h2>
            <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-4">
              {category.items.map((item) => (
                <div key={item} className="aspect-video bg-gray-800 rounded-md overflow-hidden">
                  <img
                    src={`/placeholder.svg?height=200&width=300&text=Movie ${item}`}
                    alt={`Movie ${item}`}
                    className="w-full h-full object-cover"
                  />
                </div>
              ))}
            </div>
          </div>
        ))}
      </div>
    </div>
  )
}
