
gam.pyxplot.png: gam.data.txt gam.tab.txt Makefile
	echo '\
	set terminal png ;\
	set output "$@" ;\
	set xlabel "$$x$$" ;\
	set ylabel "$$y$$" ;\
	set tics out ;\
	set title "Gamma and LnGamma function (app.)" ;\
	set key right bottom ;\
	plot [-5:5] [-5:5] "gam.data.txt" index 0 using 1:2 with lines title "Gamma(x)",\ \n\
	"gam.data.txt" every ::50::100  using 1:3 with lines title "lnGamma(x)",\
	"gam.tab.txt" using 1:2 with points pointtype 2 title "Tabulated Gamma", \
	"gam.tab.txt" using 1:3 with points pointtype 3 title "Tabulated lnGamma"\
	'| tee log.pyx.gpi | pyxplot

gam.tab.txt: Makefile
	>$@
	echo 1	1	0 >>$@
	echo 2	1	0 >>$@
	echo 3	2	0.69314718055994530941723212145818 >>$@
	echo 4  6	1.7917594692280550008124773583807 >>$@


gam.data.txt: main.exe
	mono $< > $@

all: Out.txt
	cat $<

Out.txt: main.exe
	 mono main.exe > Out.txt

main.exe: main.cs
	mcs -target:exe -out:$@ $<

clean:
	rm -f main.exe Out.txt
