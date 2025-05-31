// GrowPal - AI-Powered Seasonal Farming Assistant
import React, { useState } from 'react';

export default function GrowPal() {
  const [location, setLocation] = useState('');
  const [soilType, setSoilType] = useState('loamy');
  const [experience, setExperience] = useState('beginner');
  const [recommendations, setRecommendations] = useState([]);

  const cropRecommendations = () => {
    let crops;
    switch (soilType) {
      case 'sandy':
        crops = [
          { name: 'Carrots', plan: 'Water 3x/week, harvest in 70 days' },
          { name: 'Peppers', plan: 'Fertilize every 2 weeks, harvest in 60 days' },
          { name: 'Cucumbers', plan: 'Daily watering, harvest in 55 days' }
        ];
        break;
      case 'clay':
        crops = [
          { name: 'Cabbage', plan: 'Water weekly, harvest in 90 days' },
          { name: 'Potatoes', plan: 'Fertilize monthly, harvest in 100 days' },
          { name: 'Spinach', plan: 'Keep moist, harvest in 45 days' }
        ];
        break;
      default:
        crops = [
          { name: 'Tomatoes', plan: 'Water every 2 days, harvest in 80 days' },
          { name: 'Zucchini', plan: 'Fertilize weekly, harvest in 50 days' },
          { name: 'Lettuce', plan: 'Shaded area, harvest in 30 days' }
        ];
    }
    setRecommendations(crops);
  };

  return (
    <div className="p-6 max-w-xl mx-auto">
      <h1 className="text-3xl font-bold mb-4">GrowPal 🌱</h1>

      <div className="space-y-4">
        <input
          type="text"
          placeholder="Enter your location"
          value={location}
          onChange={(e) => setLocation(e.target.value)}
          className="w-full p-2 border rounded"
        />

        <select
          value={soilType}
          onChange={(e) => setSoilType(e.target.value)}
          className="w-full p-2 border rounded"
        >
          <option value="loamy">Loamy</option>
          <option value="sandy">Sandy</option>
          <option value="clay">Clay</option>
        </select>

        <select
          value={experience}
          onChange={(e) => setExperience(e.target.value)}
          className="w-full p-2 border rounded"
        >
          <option value="beginner">Beginner</option>
          <option value="intermediate">Intermediate</option>
          <option value="expert">Expert</option>
        </select>

        <button
          onClick={cropRecommendations}
          className="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700"
        >
          Get Recommendations
        </button>
      </div>

      {recommendations.length > 0 && (
        <div className="mt-6 space-y-4">
          {recommendations.map((crop, index) => (
            <div key={index} className="p-4 border rounded shadow">
              <h2 className="text-xl font-semibold">{crop.name}</h2>
              <p>{crop.plan}</p>
            </div>
          ))}
        </div>
      )}
    </div>
  );
}
