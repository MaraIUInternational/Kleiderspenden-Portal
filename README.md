# Kleiderspenden-Portal
Umsetzung einer Webanwendung für Kleiderspenden [ Projekt für die Uni ]
kleiderspenden-portal/
├── public/
│   ├── index.html
│   └── logo.svg
├── src/
│   ├── components/
│   │   ├── Header.js
│   │   ├── Footer.js
│   │   ├── DonationForm.js
│   │   └── ConfirmationPage.js
│   ├── App.js
│   └── index.js
├── package.json
└── tailwind.config.js
// Header.js
import React from 'react';
import logo from '../logo.svg';

const Header = () => (
  <header className="bg-blue-600 text-white p-4">
    <div className="container mx-auto flex justify-between items-center">
      <img src={logo} alt="Logo" className="h-12" />
      <h1 className="text-2xl font-bold">Kleiderspenden Portal</h1>
      <nav>
        <ul className="flex space-x-4">
          <li><a href="/">Home</a></li>
          <li><a href="/spenden">Spenden</a></li>
          <li><a href="/ueber-uns">Über uns</a></li>
        </ul>
      </nav>
    </div>
  </header>
);

export default Header;
// App.js
import React from 'react';
import Header from './components/Header';
import Footer from './components/Footer';
import DonationForm from './components/DonationForm';

const App = () => (
  <div className="flex flex-col min-h-screen">
    <Header />
    <main className="flex-grow container mx-auto p-4">
      <DonationForm />
    </main>
    <Footer />
  </div>
);

export default App;
// DonationForm.js
import React, { useState } from 'react';

const DonationForm = () => {
  const [donationType, setDonationType] = useState('');
  const [address, setAddress] = useState('');
  const [clothingType, setClothingType] = useState('');
  const [crisisRegion, setCrisisRegion] = useState('');
  const [zipCode, setZipCode] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    // Validierung und Verarbeitung der Formulardaten
    // Weiterleitung zur Bestätigungsseite
  };

  return (
    <form onSubmit={handleSubmit} className="space-y-4">
      <div>
        <label className="block">Spendenart:</label>
        <select
          value={donationType}
          onChange={(e) => setDonationType(e.target.value)}
          className="w-full p-2 border rounded"
        >
          <option value="">Bitte wählen</option>
          <option value="office">Übergabe an der Geschäftsstelle</option>
          <option value="pickup">Abholung</option>
        </select>
      </div>

      {donationType === 'pickup' && (
        <div>
          <label className="block">Abholadresse:</label>
          <input
            type="text"
            value={address}
            onChange={(e) => setAddress(e.target.value)}
            className="w-full p-2 border rounded"
          />
          <input
            type="text"
            value={zipCode}
            onChange={(e) => setZipCode(e.target.value)}
            placeholder="PLZ"
            className="w-full p-2 border rounded mt-2"
          />
        </div>
      )}

      <div>
        <label className="block">Art der Kleidung:</label>
        <input
          type="text"
          value={clothingType}
          onChange={(e) => setClothingType(e.target.value)}
          className="w-full p-2 border rounded"
        />
      </div>

      <div>
        <label className="block">Krisengebiet:</label>
        <select
          value={crisisRegion}
          onChange={(e) => setCrisisRegion(e.target.value)}
          className="w-full p-2 border rounded"
        >
          <option value="">Bitte wählen</option>
          <option value="region1">Region 1</option>
          <option value="region2">Region 2</option>
          {/* Weitere Regionen */}
        </select>
      </div>

      <button type="submit" className="bg-blue-600 text-white p-2 rounded">
        Spende registrieren
      </button>
    </form>
  );
};

export default DonationForm;
