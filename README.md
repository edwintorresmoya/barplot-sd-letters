# barplot-sd-letters

meantmp2 = tapply(temperatura$value,temperatura$variable ,mean)
sdtmp2 = tapply(temperatura$value,temperatura$variable ,sd)

meantmp = as.data.frame(meantmp2)
sdtmp = as.data.frame(sdtmp2)

meantmp$sdtmp = sdtmp$sdtmp2

meantmp$texto = c("a", "b", "c")

merge(meantmp, sdtmp, by = row.names)

ggplot(meantmp, aes(x = row.names(meantmp), y = meantmp2)) + geom_bar(stat = "identity") + 
    geom_errorbar(aes(ymax = meantmp2 + sdtmp, ymin = meantmp2 - sdtmp), position = dodge, width = 0.5) + 
    geom_text(aes(label = texto), vjust = -3, size = 3.5)
