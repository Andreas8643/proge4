# proge4
a, b, c, d, ä = 0, 0, 0, 0, 0
f = open("sonad.txt", "r", encoding="UTF-8")
fail = f.readlines()
sõnad = [el.strip("\n").upper() for el in fail]
f.close()
tähed = ["A", 0, "B", 0, "C", 0, "D", 0, "E", 0, "F", 0, "G", 0, "H", 0, "I", 0, "J", 0, "K", 0, "L", 0, "M", 0, "N", 0, "O", 0, "P", 0, "Q", 0, "R", 0, "S", 0, "Š", 0, "Z", 0, "Ž", 0, "T", 0, "U", 0, "V", 0, "W", 0, "Õ", 0, "Ä", 0, "Ö", 0, "Ü", 0, "X", 0, "Y", 0]    
while True:
    d = 0
    L5 = ["A", 0, "B", 0, "C", 0, "D", 0, "E", 0, "F", 0, "G", 0, "H", 0, "I", 0, "J", 0, "K", 0, "L", 0, "M", 0, "N", 0, "O", 0, "P", 0, "Q", 0, "R", 0, "S", 0, "Š", 0, "Z", 0, "Ž", 0, "T", 0, "U", 0, "V", 0, "W", 0, "Õ", 0, "Ä", 0, "Ö", 0, "Ü", 0, "X", 0, "Y", 0]    
    õiged = []
    sisend = input().upper()
    b = 0
    #teeb õigete sõnade listi
    for sõna in sõnad:
        L1 = []
        L2 = []
        vale = 0
        L1.extend(sisend)
        L2.extend(sõna)
        if len(L1) != len(L2):
            vale += 1
        for el in range(len(L1)):
            try:
                if L1[0] != "_":
                    if L1[0] != L2[0]:
                        vale += 1
                        continue
                L1.pop(0)
                L2.pop(0)
            except:
                vale += 1
        if vale == 0:
            õiged.append(sõna)
    if len(õiged) == 1:
        print(õiged[0])
        sisend2 = input()
        if sisend2 == õiged[0]:
            break
    #tähtede esinemine sõnades
    for el in õiged:
        L3 = []
        L3.extend(el)
        a = 0
        for i in range(len(L3)):
            try:
                tähed[tähed.index(L3[i]) + 1] += 1
            except:
                continue
    #vaatab, mitu korda tähed esinevad, et vältida programmi pakkumast tähte, mis on igas sõnas
    b = 0
    L4 = []
    for sõna2 in õiged:
        ä = 0
        L4.extend(sõna2)
        L4 = list(set(L4))
        for l in L4:
            ä = L5.index(l)
            L5[ä - 1] += 1
    #eemaldab tähtede listist kõik tähed, mis on olemas igas sõnas
    for i in range(len(L5)):
        try:
            if len(õiged) == L5[i]:
                u = index(tähed[i])
                del tähed[u - 1:u + 1]
        except:
            continue
    #vaatab mis täht on kõige populaarsem
    for nujh in tähed:
        try:
            if nujh > b:
                b = nujh
        except:
            continue
    #kui tähti enam sõnades pole, eemaldab need lsitist
    for i in range(len(tähed)):
        if tähed[d] == 0:
            del tähed[d - 1:d + 1]
            d -= 2
        d += 1
    #väljastab populaarseima tähe ja kustutab selle listist
    c = tähed.index(b)
    print(tähed[c-1])
    del tähed[c - 1:c + 1]
    #resetib kõik tähtede kordumised 0iks
    for o in range(len(tähed)):
        try:
            tähed[o] += 1
            tähed[o] = 0
        except:
            continue
