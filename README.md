import SwiftUI



struct Mood: Identifiable {
    let id = UUID()
    let emoji: String
    let date: Date
}

struct ContentView: View {
    
    @State private var moods: [Mood] = []
    
    let moodEmojis = ["😊", "😐", "😢", "😡", "🤩"]
    
    var body: some View {
        NavigationView {
            VStack {
                
                Text("How are you feeling?")
                    .font(.title)
                    .padding()
                
                HStack(spacing: 20) {
                    ForEach(moodEmojis, id: \.self) { emoji in
                        Button(action: {
                            addMood(emoji)
                        }) {
                            Text(emoji)
                                .font(.largeTitle)
                        }
                    }
                }
                .padding()
                
                List(moods) { mood in
                    HStack {
                        Text(mood.emoji)
                            .font(.largeTitle)
                        Spacer()
                        Text(mood.date, style: .time)
                            .foregroundColor(.gray)
                    }
                }
            }
            .navigationTitle("Mood Tracker")
        }
    }
    
    func addMood(_ emoji: String) {
        let newMood = Mood(emoji: emoji, date: Date())
        moods.insert(newMood, at: 0)
    }
}

#Preview {
    ContentView()
}
## How it looks like 
<img width="613" height="391" alt="Screenshot 2026-01-28 at 12 01 02 PM" src="https://github.com/user-attachments/assets/897bada5-e98c-4218-b248-05092c44accb" />

