# Mood Journal App

A modern, AI-powered mood tracking application that helps you understand and reflect on your emotional well-being. Built with Supabase, Hugging Face AI, and IntaSend payment integration.

## 🌟 Features

- **Daily Mood Tracking**: Record your mood with customizable emotional states
- **AI-Powered Insights**: Get intelligent analysis of your mood patterns using Hugging Face AI
- **Secure Authentication**: User management powered by Supabase Auth
- **Journal Entries**: Add detailed notes to your mood entries
- **Data Visualization**: View mood trends and patterns over time
- **Premium Features**: Unlock advanced insights with IntaSend payment integration
- **Responsive Design**: Works seamlessly on desktop and mobile devices

## 🛠️ Tech Stack

- **Backend**: Supabase (PostgreSQL database, authentication, and storage)
- **AI Integration**: Hugging Face Transformers for mood analysis
- **Payment Processing**: IntaSend for premium feature subscriptions
- **Frontend**: React.js with modern CSS/styling framework
- **Deployment**: Vercel/Netlify (or similar platform)

## 🚀 Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- Supabase account
- Hugging Face API account
- IntaSend merchant account

### Installation

1. Clone the repository:
```bash
git clone https://github.com/your-username/mood-journal-app.git
cd mood-journal-app
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
Create a `.env` file in the root directory with the following variables:

```env
REACT_APP_SUPABASE_URL=your_supabase_project_url
REACT_APP_SUPABASE_ANON_KEY=your_supabase_anon_key
REACT_APP_HUGGING_FACE_API_KEY=your_hugging_face_api_key
REACT_APP_INTASEND_PUBLIC_KEY=your_intasend_public_key
REACT_APP_INTASEND_SECRET_KEY=your_intasend_secret_key
```

4. Set up your Supabase database:
- Create a new project in Supabase
- Run the following SQL to set up the necessary tables:

```sql
-- Mood entries table
CREATE TABLE mood_entries (
  id UUID DEFAULT uuid_generate_v4() PRIMARY KEY,
  user_id UUID REFERENCES auth.users(id),
  mood_score INTEGER NOT NULL,
  mood_label TEXT NOT NULL,
  journal_entry TEXT,
  ai_insights JSONB,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT TIMEZONE('utc'::text, NOW())
);

-- User profiles table
CREATE TABLE user_profiles (
  id UUID REFERENCES auth.users(id) PRIMARY KEY,
  username TEXT UNIQUE,
  full_name TEXT,
  subscription_tier TEXT DEFAULT 'free',
  subscription_end_date TIMESTAMP WITH TIME ZONE,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT TIMEZONE('utc'::text, NOW())
);

-- Enable Row Level Security
ALTER TABLE mood_entries ENABLE ROW LEVEL SECURITY;
ALTER TABLE user_profiles ENABLE ROW LEVEL SECURITY;

-- Create policies for mood_entries
CREATE POLICY "Users can view their own mood entries" 
ON mood_entries FOR SELECT 
USING (auth.uid() = user_id);

CREATE POLICY "Users can insert their own mood entries" 
ON mood_entries FOR INSERT 
WITH CHECK (auth.uid() = user_id);

CREATE POLICY "Users can update their own mood entries" 
ON mood_entries FOR UPDATE 
USING (auth.uid() = user_id);

CREATE POLICY "Users can delete their own mood entries" 
ON mood_entries FOR DELETE 
USING (auth.uid() = user_id);

-- Create policies for user_profiles
CREATE POLICY "Users can view their own profile" 
ON user_profiles FOR SELECT 
USING (auth.uid() = id);

CREATE POLICY "Users can update their own profile" 
ON user_profiles FOR UPDATE 
USING (auth.uid() = id);
```

5. Start the development server:
```bash
npm start
```

## 🔧 Configuration

### Supabase Setup
1. Create a new project at [Supabase](https://supabase.io)
2. Get your project URL and API key from Settings > API
3. Enable Email authentication in Authentication > Settings

### Hugging Face Setup
1. Create an account at [Hugging Face](https://huggingface.co)
2. Get your API token from Settings > Access Tokens
3. The app uses a sentiment analysis model (e.g., distilbert-base-uncased-finetuned-sst-2-english)

### IntaSend Setup
1. Create a merchant account at [IntaSend](https://intasend.com)
2. Get your public and secret keys from the dashboard
3. Configure webhooks for payment verification

## 📱 Usage

1. **Sign Up/Login**: Create an account or login using Supabase authentication
2. **Record Your Mood**: Select your current mood and add optional journal text
3. **View Insights**: Get AI-powered analysis of your mood patterns
4. **Track Progress**: View historical data and trends in your dashboard
5. **Upgrade (Optional)**: Subscribe to premium features for deeper insights

## 🎨 Customization

The app can be customized by modifying:
- Color scheme in CSS variables
- Mood labels and emojis in `src/constants/moodOptions.js`
- AI model used for analysis in `src/services/aiService.js`
- Payment plans in `src/components/PaymentPlans.js`

## 🤝 Contributing

We welcome contributions! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

## 🙏 Acknowledgments

- Supabase for the excellent backend-as-a-service
- Hugging Face for making AI models accessible
- IntaSend for seamless payment processing in Africa
- React community for amazing tools and libraries
