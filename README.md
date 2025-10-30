# wbudowane_pakiety
wbudowane_pakiety

import csv
import sys

def main():
    if len(sys.argv) < 3:
        print("Użycie: python reader.py <plik_wejsciowy> <plik_wyjsciowy> <zmiana_1> <zmiana_2> <zmiana_n>")
        sys.exit(1)

    input_file = sys.argv[1]
    output_file = sys.argv[2]
    changes = sys.argv[3:]

    with open(input_file, newline='', encoding='utf-8') as csvfile:
        reader = list(csv.reader(csvfile))

    for change in changes:
        try:
            x, y, value = change.split(',', 2)
            x = int(x)
            y = int(y)
            reader[y][x] = value
        except Exception as e:
            print(f"Błąd przy przetwarzaniu zmiany '{change}': {e}")

    print("\nZmieniona zawartość pliku CSV:")
    for row in reader:
        print(','.join(row))

    with open(output_file, 'w', newline='', encoding='utf-8') as csvfile:
        writer = csv.writer(csvfile)
        writer.writerows(reader)

    print(f"\nPlik został zapisany jako: {output_file}")

if __name__ == "__main__":
    main()
#############################
W pliku in.csv dane: 
drzwi,3,7,0
kanapka,12,5,1
pedzel,22,34,5
plakat,czerwony,8,kij
