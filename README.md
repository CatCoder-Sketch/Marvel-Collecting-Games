# Marvel-Collecting-Games
import SwiftUI

// Sample Marvel characters
let allMarvelCharacters = [
    "Iron Man",
    "Spider-Man",
    "Captain America",
    "Thor",
    "Black Widow",
    "Hulk",
    "Doctor Strange",
    "Black Panther",
    "Scarlet Witch",
    "Loki"
]

struct ContentView: View {
    @State private var collection: [String] = []
    @State private var currentCharacter: String = ""

    var body: some View {
        NavigationView {
            VStack(spacing: 20) {
                Text("🎯 Tap to Collect a Marvel Hero")
                    .font(.headline)
                
                Button(action: collectCharacter) {
                    Text("Collect Hero")
                        .font(.title2)
                        .padding()
                        .frame(maxWidth: .infinity)
                        .background(Color.red)
                        .foregroundColor(.white)
                        .cornerRadius(10)
                }

                if !currentCharacter.isEmpty {
                    Text("You collected: \(currentCharacter)!")
                        .font(.title3)
                        .padding()
                        .transition(.slide)
                }

                Divider()

                Text("🦸‍♂️ Your Collection")
                    .font(.headline)

                List {
                    ForEach(collection, id: \.self) { character in
                        Text(character)
                    }
                }
            }
            .padding()
            .navigationTitle("Marvel Collector")
        }
    }

    func collectCharacter() {
        let newCharacter = allMarvelCharacters.randomElement() ?? "Unknown Hero"
        currentCharacter = newCharacter

        if !collection.contains(newCharacter) {
            collection.append(newCharacter)
        }
    }
}
