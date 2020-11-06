# R_theme
Summary of common themes in ggplot2

<code>
library(ggplot2)
library(ggsci)

df <- diamonds
df_color <- unique(df$color)
df$color <- factor(df$color,levels=df_color)
colortype <- ifelse((df_color == "D"), "red", "black")

theme_1 <- 
  theme(
    axis.text.x=element_text(size=5,face="bold",angle=20,vjust=.5,hjust=.5,colour=colortype),
    axis.text.y=element_text(size=6,face="bold"),
    axis.title.x=element_blank(),
    legend.text=element_text(size=6,face="bold"),
    legend.title=element_blank(),
    legend.background = element_rect(colour = "NA"),
    legend.key.size = unit(0.75, "lines"),
    strip.background = element_rect(fill = "transparent"),
    strip.text = element_text(size=6.5,face="bold")
    
  )

df <- subset(df,(clarity == c("SI2","SI1","VS1","VS2")))
p <-  ggplot(df,aes(color,depth,fill=cut))+
      geom_histogram(stat="identity",position="stack")+
      facet_grid(clarity~.)+
      theme_1+
      scale_fill_nejm()
p
</code>

  
  
