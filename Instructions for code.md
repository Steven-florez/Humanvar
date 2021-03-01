# Instructions code

Import freq.df Allele Frequency Data.
```
freq <- read.table('freq.df', header=T)
```
Histograms
```
hist(freq$Allele_A)
```
hist(freq$Allele_A, breaks=20)
```
Creating Scatterplots
````
plot(freq$Allele_A, freq$lat)
```
plot(freq$Allele_A, freq$lat, xlab="f(A) rs1426654", ylab="Latitude", pch=16)
```
plot(freq$Allele_A, freq$lat, xlab="f(A) rs1426654", 
        ylab="Latitude", pch=16, cex=0.8, 
        col=freq$popname, xlim=c(0.55,0.95))
```
myColors <- c(AFR='red', AMR='blue', EAS='darkgreen', EUR='salmon', SAS='black')
plot(freq$Allele_A, freq$lat, xlab="f(A) rs1426654", ylab="Latitude", 
    pch=16, cex=0.8, col=myColors[freq$superpop], xlim=c(0, 1))
```
plot(freq$Allele_A, freq$lat, xlab="f(A) rs1426654", ylab="Latitude", 
        pch=16, cex=0.8, col=myColors[freq$superpop], xlim=c(0, 1))
legend('topleft', c('African', 'Admixed American', 'East Asia', 'European', 'South Asian'), 
        cex=0.8, col=c('red','blue','darkgreen','salmon','black'), pch=16, inset=0.02)
title(main="Latitudinal Variation in f(A) at rs1426654 among 26 Human Populations", cex.main=1)
```
Plotting the data on a geo map
download map packs if needed
```
map('worldHires', xlim=c(-120,142), ylim=c(-12,72), col='gray', fill=FALSE)
box()
```
Plot human pops on the map
```
map('worldHires', xlim=c(-120,142), ylim=c(-12,72), col='gray', fill=FALSE)
points(freq$long, freq$lat, pch=16, col="salmon")
box()
```

Using pie charts to disply allele freq
```
 map('worldHires', xlim=c(-120,142), ylim=c(-12,72), col='gray', fill=FALSE)

add.pie(z=c(0.104, 0.895), x=-59.5412, y=13.1776, radius=192/100, 
            col=c(alpha("orange", 0.6), alpha("blue", 0.6)), labels=")
box()
```
 map('worldHires', xlim=c(-120,142), ylim=c(-15,72), col='gray', fill=FALSE)
 for (i in 1:26){add.pie(z=c(freq$Allele_A[i], freq$Allele_G[i]), x=freq$long[i], y=freq$lat[i], 
        radius=freq$N_CHR[i]/100, col=c(alpha("orange", 0.6), alpha("blue", 0.6)), labels="")
  i=i+1
}
box()
 
```
add legend a labels
```
 map('worldHires', xlim=c(-120,142), ylim=c(-15,72), col='gray', fill=FALSE)
 for (i in 1:26){add.pie(z=c(freq$Allele_A[i], freq$Allele_G[i]), x=freq$long[i], y=freq$lat[i], 
        radius=freq$N_CHR[i]/100, col=c(alpha("orange", 0.6), alpha("blue", 0.6)), labels="")
  i=i+1
}
box()
legend('topright', bty='1', c("Freq. Allele A", "Freq. Allele G"), 
        pch=16, col=c(alpha("orange", 0.6), alpha("blue", 0.6)), pt.cex=1, cex=0.7)
 title(main="Global Distribution of rs1426654 Alleles", font.main=1, cex.main=0.9)