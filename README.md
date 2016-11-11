# barplot-sd-letters

modelo = aov((temperatura$value) ~ temperatura$variable)
tuk = HSD.test(modelo, 'temperatura$variable')$groups
tuk$sd = HSD.test(modelo, 'temperatura$variable')$means$std

ggplot(tuk, aes(x = trt, y = means, fill = trt)) + geom_bar(stat = "identity") + 
    geom_errorbar(aes(ymax = means + sd, ymin = means - sd), position = dodge, width = 0.5) + 
    geom_text(aes(label = M), vjust = -3, size = 4)
