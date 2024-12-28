import React, { useState } from 'react';
import { Rocket, Code, Brain, Cloud, Database, Shield } from 'lucide-react';
import { BarChart, Bar, XAxis, YAxis, CartesianGrid, Tooltip, ResponsiveContainer } from 'recharts';

const skillsData = [
  { category: 'Frontend', value: 85, color: '#FF4D4D' },
  { category: 'Backend', value: 80, color: '#4D79FF' },
  { category: 'AI/ML', value: 75, color: '#FFB84D' },
  { category: 'Cloud', value: 70, color: '#4DB8FF' },
  { category: 'DevOps', value: 65, color: '#4DFF88' }
];

const technologies = [
  { name: 'JavaScript', level: 'Avanzado', icon: Code, years: 4 },
  { name: 'Python', level: 'Avanzado', icon: Brain, years: 3 },
  { name: 'AWS', level: 'Intermedio', icon: Cloud, years: 2 },
  { name: 'React', level: 'Avanzado', icon: Code, years: 3 },
  { name: 'Node.js', level: 'Avanzado', icon: Database, years: 4 },
  { name: 'TensorFlow', level: 'Intermedio', icon: Brain, years: 2 }
];

const achievements = [
  { title: 'Proyectos Completados', value: '100+', icon: Rocket },
  { title: 'Tasa de Éxito', value: '90%', icon: Shield },
  { title: 'Competencias Ganadas', value: '10', icon: Trophy }
];

export default function DevProfile() {
  const [hoveredSkill, setHoveredSkill] = useState(null);

  return (
    <div className="min-h-screen bg-gradient-to-br from-gray-900 to-gray-800 text-white p-8">
      {/* Header Section */}
      <div className="text-center mb-12">
        <h1 className="text-5xl font-bold mb-4 bg-clip-text text-transparent bg-gradient-to-r from-red-500 to-orange-500">
          Alexander
        </h1>
        <h2 className="text-2xl text-gray-300">Senior Full Stack & AI Engineer</h2>
        <p className="text-lg text-gray-400 mt-2">Costa Rica 🌴</p>
      </div>

      {/* Skills Chart */}
      <div className="bg-gray-800 rounded-lg p-6 mb-8 shadow-xl">
        <h3 className="text-2xl font-bold mb-6 text-center">Habilidades Técnicas</h3>
        <div className="h-64">
          <ResponsiveContainer width="100%" height="100%">
            <BarChart data={skillsData}>
              <CartesianGrid strokeDasharray="3 3" />
              <XAxis dataKey="category" />
              <YAxis />
              <Tooltip />
              <Bar dataKey="value" fill="#8884d8">
                {skillsData.map((entry, index) => (
                  <Cell key={index} fill={entry.color} />
                ))}
              </Bar>
            </BarChart>
          </ResponsiveContainer>
        </div>
      </div>

      {/* Technologies Grid */}
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mb-8">
        {technologies.map((tech) => (
          <div
            key={tech.name}
            className="bg-gray-800 rounded-lg p-6 transform hover:scale-105 transition-transform"
            onMouseEnter={() => setHoveredSkill(tech.name)}
            onMouseLeave={() => setHoveredSkill(null)}
          >
            <div className="flex items-center mb-4">
              <tech.icon className="w-8 h-8 text-blue-400 mr-3" />
              <div>
                <h4 className="text-xl font-semibold">{tech.name}</h4>
                <p className="text-gray-400">{tech.level}</p>
              </div>
            </div>
            <div className="w-full bg-gray-700 rounded-full h-2.5">
              <div
                className="bg-blue-500 h-2.5 rounded-full transition-all duration-500"
                style={{
                  width: hoveredSkill === tech.name ? '100%' : '85%'
                }}
              ></div>
            </div>
            <p className="text-gray-400 mt-2">{tech.years} años de experiencia</p>
          </div>
        ))}
      </div>

      {/* Achievements */}
      <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
        {achievements.map((achievement) => (
          <div key={achievement.title} className="bg-gray-800 rounded-lg p-6 text-center">
            <achievement.icon className="w-12 h-12 text-yellow-400 mx-auto mb-4" />
            <h4 className="text-xl font-semibold mb-2">{achievement.title}</h4>
            <p className="text-3xl font-bold text-blue-400">{achievement.value}</p>
          </div>
        ))}
      </div>
    </div>
  );
}
