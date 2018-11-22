

---
title: "Skills Chart"
author: "John Houghton"
date: "11/21/2018"
output: html_document
---




```r
library(tidyverse)
# Create data (could be way easier but it's late)
value1 <- abs(rnorm(6))*2
don <- data.frame(
  x=LETTERS[1:24], 
  val=c( value1, value1+1+rnorm(6, 14,1) ,value1+1+rnorm(6, sd=1) ,value1+1+rnorm(6, 12, 1) ),
  grp=rep(c("grp1", "grp2", "grp3", "grp4"), each=6)
) %>%
  arrange(val) %>%
  mutate(x=factor(x, x))


# With a bit more style
ggplot(don) +
  geom_segment( aes(x=x, xend=x, y=0, yend=val), color="grey") +
  geom_point( aes(x=x, y=val, color=grp), size=3 ) +
  coord_flip()+
  #theme_ipsum() +
  theme(
    legend.position = "none",
    panel.border = element_blank(),
    panel.spacing = unit(0.1, "lines"),
    strip.text.x = element_text(size = 8)
  ) +
  xlab("") +
  ylab("Value of Y") +
  facet_wrap(~grp, ncol=1, scale="free_y")
```

![plot of chunk unnamed-chunk-2](https://i.imgur.com/Jl70HwD.png)

