Processing Jobs

hacker@processes~listing-processes:~$ ps -efww
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 13:51 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 13:51 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 13:51 ?        00:00:00 /challenge/21609-run-16015
root         135     132  0 13:51 ?        00:00:00 sleep 6h
hacker       137       0  0 13:52 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       143     137  0 13:52 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       152     143  0 13:52 pts/0    00:00:00 ps -efww
hacker@processes~listing-processes:~$ ps -efww | grep /challenge
root         132       1  0 13:51 ?        00:00:00 /challenge/21609-run-16015
hacker       154     143  0 13:53 pts/0    00:00:00 grep --color=auto /challenge
hacker@processes~listing-processes:~$ /challenge/21609-run-16015
Yahaha, you found me! Here is your flag:
pwn.college{s81IEXgTmNzK4OhnXKg_7TgVw9_.QX4MDO0wSNxIzNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').



hacker@processes~killing-processes:~$ ps -efww | grep /challenge/dont_run
hacker       136     135  0 13:54 ?        00:00:00 /challenge/dont_run
hacker       177     161  0 13:57 pts/1    00:00:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ ps -efww | grep /challenge/dont_run
hacker       179     161  0 13:57 pts/1    00:00:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ kill 179
bash: kill: (179) - No such process
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{cOQFV7c8UHLnpJxEx85bWO4l29P.QXyQDO0wSNxIzNzEzW}






hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{0zuWCFWSj9W7jT0KMXVu98CvfIU.QXzQDO0wSNxIzNzEzW}




hacker@processes~killing-misbehaving-processes:~$ ps auxww | grep /challenge/decoy
hacker       217  0.0  0.0 230696  2560 pts/3    S+   14:04   0:00 grep --color=auto /challenge/decoy
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{Khx2XSyB1k-q2nLMsYxfJvGa5B.aIkLbcZ7VYzXTAl8-jDt}
pwn.college{KAfLwo-Y3Ww2jq2YYfZVba8Gauo3hzpZrZwrXogaaVBs12j}
pwn.college{sJM9jqmsm5jCuO-Rhc4Z5dxh1L2am6LDU4w2QAoe9n6wFOv}
pwn.college{bErbSlZTSvBY6.f6upy8dx8CDfb2da7YwkRzNo2swlNaysB}
pwn.college{-uC5N1ivT3rN9P5qrhxAAaYZiMdJH4bwR.tAMfJRiizXB4k}
pwn.college{VpK4lpn9.G5skEn2y9SfINldRv8rRrSw7J4WmH9Tv0UZKqS}
pwn.college{6gcOjy.PlF1UR.kB6j5mDFRv7DDD.K9oI3U5GLNhLFpXdhn}
pwn.college{SvDFNAAcaz28Di5yxPIMHDNiUgmzjuO1HX3ihIrph.uTpof}
pwn.college{xkaxyNq1-2jrStH1zsEQX3t.ZNWJlitqa6LqqCK6QCQnKe7}
pwn.college{FIJ1c27CusBc4JGq-KOg2Kqgt3S-JmW3vU.hswrX5MLW.ku}
pwn.college{tFjzLHq7B72oGhorVxDONc7pWykhoj5oNdU3TObLVW-Y.px}
pwn.college{C46hDe7Za7kaSkMzO7R.KYzs-dxaulg4QkBZC1GcBve5frt}
pwn.college{fO0o-dQxOtULpjrMQXk9iuqgajkPBtvs1VzvFPISHl0q6bQ}
pwn.college{WWPBMDleIl-q5a-xWt3xkCS3DEnD9.YROGEZYhIqJC6E2gw}
pwn.college{w9djpz.1L9D420AWkAnZ7PkZNVoSG5RrRmMOTkK20IPvt3q}
pwn.college{rSodCyPT7fbvtCipsJMqk2JK9mFrHvgpgDiUOSc34r6hHra}
pwn.college{lKvhJ5dfPbWyG1S7FHzakPzbfyxTn.-fPOiv-.0EYkbKa9m}
pwn.college{Q.TJHoGrmTE6gBNH.zZr8j9OHFHBRxRKwjJaoEwxbfs3iPg}
pwn.college{ntT5ArYead2uvlteJEZmQ1F3K6EQit78KtKojiJwq9jIBdJ}
pwn.college{BmdGrsGQWE3uGYOFqRTX4M7cVEfB0RbmGmo7YpEGBnDFLv8}
pwn.college{qdNMz8BGc1JySphCiNwQqmlKKYHauwWAUPzO-goxO823rHa}
pwn.college{5lhXJNSpZ.HkDePvsQgUYG9MUAcHkDpA6GJJTyoha9VNexv}
pwn.college{KI0kOVg0n9VKglR9SRschCSYOywgvaQMVOi7M89TJi5jV9z}
pwn.college{f4xJCTeVGI1X0Wc1ln14zkUbDNCySuzsugbZJiU-nfoN80b}
pwn.college{7E4la-Hlv-n0DLHc1yrIjc1VdnsZ.JIML8wfKZECOe4qF4g}
pwn.college{PkCs9l7oiYL7QalmUtL-Avs2XpDUTjZvNTLxMdb.efjtsdF}
pwn.college{agun.TiLOg9CHJkUmcenQ4aUE7BWIy84P4EYInzA5AEbpws}
pwn.college{MfdQREbke9DkA9p4DnX4d6f7oXG5Uw3guz8ULwDz0pZX127}
pwn.college{ypbEDbBWRw1pQqEFbocoswOBuN77sgKvQ7DF9hoCXmCSooZ}
pwn.college{0Zo87Pr20HgUcDpc8jQX5S6J1uHhfSOn8hwIRXaTv-qOdz3}
pwn.college{U5isYPj8as8tWXUwSDuvwKkN5u6ClR.5PidxHZJvHNznxAP}
pwn.college{KV4rPFjD25fiPvSa-RgTNdtaB0hqICVjXauYdAaZBvQzQDr}
pwn.college{znS5g3rdZ2lrNCgABhyeNK2iz2.7ST1tY5qFnevpQAqqGWH}
pwn.college{rh3IuPJl91DKqQivWoNDrKHkolyLQzpf-fWICHHAzSueZPZ}
pwn.college{AFognUvx2pZRlcczGdU8jZHDL2JYbsHJsRGiClMbeb.CYc5}
pwn.college{ColqcmYlL1QERfLir5aN-x-7cCDY-l.hB77m7vKEDfnHhPm}
pwn.college{mHTJ9e3Gae8lSnUI.z9ouLLwndU10miBBJm3WEa9Kszheov}
pwn.college{QKmUSt21cPKs1EX3oaJufFo.fFoYJYjMHi6ELIXXL48KD7e}
pwn.college{o68DgRsfnL5tvW5czDMZwZcPMWVpfp3xTTWLVtbitDF2U0y}
pwn.college{PoeCkNXRqkLokB.gTcLGXrtpNt.jJ1pTTMR7D2DxoILcpfX}
pwn.college{WYsnnu-4YrfP6u6GqAscpQcwLOCJFfdqkugofsuhwOBohmh}
pwn.college{2fjGL7O0k2xdOhNv1ilxxtyRyhjtFWGqPst1HAkEzXpv2S8}
pwn.college{oWVTFeLMoP0ZBXXD3PIwnMY6lkl4tG3AirZry8PJFTEmUzg}
pwn.college{iEevD52eUsFixro8CWIBMr0AYQ9VZYSJlu-4HFPKL7NDtif}
pwn.college{u08bHD-wHmX.8SVs4Bd2dK5c8ds9ffv6sU3becXBwgsA4Lr}
pwn.college{JfRhOosE5wM4HR64.po3ncJ.ylwqi1oxvngIVMkuPdVlK5q}
pwn.college{-FdHjwlW142r6MruolJVpTXOF1B48nppBWsz.2uRTs6tztb}
pwn.college{XvB0HmTy03g8ldlvN9ggO6jZnaqVqTxzUcN3SBo2wkehIBE}
pwn.college{u5Ze3hq.AhTj03JeNoZbPUk9vEKOUciEf-ftXzgQJ6fgqJv}
pwn.college{XFBTEofibIMzzz3v4I7Og45HN66l0ZJQYt.h4wFQodjD.h6}
pwn.college{YkrRZlVJshrlqqfPhLFybdAFIidqC78OE0Q6T55j-m23OOs}
pwn.college{05qy4i1cHKP.B8u13nyrzZ-s5OhzzbZ8eVJUETobn4KwKH5}
pwn.college{8QWxYrk80l1MtZsq0wIQjk-p9X4d9gVO1e6K2NxSyymQK7N}
pwn.college{hhU65ceRR6UOG03k7ToH-EQPsQFFtHAlWXJYAjZk5izrssw}
pwn.college{zo8F8Kf8HXZIqqGJ1tSx8UtXedRy1Qw2XZ-GvX2EMrATIf4}
pwn.college{jIrSZpjGBPke4ROdx6Z.cadEnDWHOnZ-icIchbgVjjGlMXo}
pwn.college{ff.DrfV.gqfapPpnGmog-QcExnRxzFI0sb9Hcuj5iOXE.Cq}
pwn.college{d4G8D24n0-56jo-lnnPN8wycMB89NCeN-aooiIdvN6mHa0z}
pwn.college{2Jx9pXQer9XfhgrgDPpmLH2eXx88UBs.uQ9r5HTwgGwcFgU}
pwn.college{GZjHhZAbFz33LWmP28sguj3VYA3.NEt2Eih36CakfT.AUCB}
pwn.college{6i3UJPyfFpyXw2a8NG0cjUw4jieHIUGrdzibvbXi.ULPSPs}
pwn.college{ipZTL9KbRlECjoKQ7blthnmMMXY2xWF6GwObB6NcJsRigbI}
pwn.college{.ieHlod5dk8e4.SHKQNe122WEmB6W2.jnal5hZTzgJ7LIBJ}
pwn.college{GTwa18KCqtQN86vxD1WaWEXRG7cN6bhdufsoC.isy9X.oUN}
pwn.college{Xd8Sc6NdkLTgzldj3cGo6f.P-2UOchz9hrW0wmLicFDA6KL}
pwn.college{2JYfv02CPh.F28PligGqejaXFzF4H4qXBnR6wqyv-.DXv7q}
pwn.college{1tU1go2Svs.dgHsXAE1vyUn3tfJQGWdqDh.g0wtZFpT1C16}
pwn.college{AqVZuQm4fvBuMSxGTUyxGkFLUCiSWaVm.jlFfU5szwiOT9K}
pwn.college{w6xzEhd.lxgHntlCg9r8duKs-lI3toV8uV.Y1OKbQ6Gu96n}
pwn.college{M7mMXu8u4UUh15ck5-NcXhr2RLXkKbPBCLlZyOYjZH2zED1}
pwn.college{JtCNGfCEy1ZSMTptqLp1kq.W--XE.3Lv9iCsLiQLTcvjzI0}
pwn.college{0VpA7yKvE7A4-1ReTk.QbuHdRTQ23U0sfXdG79-LFB4eoRl}
pwn.college{IU8DCCh9wptqiZvH3serzQGNL-pBiqm9GPJFYL9RLElc01T}
pwn.college{5FFVrtkHrgIaGYdiAqVGFBnezA9p85ojg5.dBkXlGXJ1DBe}
pwn.college{SCtpg.Cw6QUoid62EuydKNZrTCIzuAUeK8aLR28ywi-07kg}
pwn.college{SeXdwAurfo1k5y19sAGuiFekeLnQuDtkPuanOflQvKL-1xe}
pwn.college{7Se0H8N2ezIv4NnZXQfXFyjhphl7C9GOAxnLNMACqFj9txx}
pwn.college{jjd50Eoy.WL4.341eOn1dLnQqNIdrM9zuGBvFWflBj27hON}
pwn.college{EuaEtoqoUAKTowdeDd6gfMsmTq4vgiN5wzdaGdCxh0Y2.ZK}
pwn.college{A5Crj9NhoQtZTNpnRD5FAtM3uAExIdVr6V16.IcqR2RGdHW}
pwn.college{N9NulkxaC0hHx016OxV7VBu4.bh-lW7kC5U4-1ZR25Ovih9}
pwn.college{7fuJJAfr66X3Z3UNZznVL1klziH3EKibG-.bXoJH8LsX4Ot}
pwn.college{Wy.XLVcPPH7RS8DQK6dOmopam1nve19db0.7uPmY.UysqaC}
pwn.college{WdqUd73nQTlRN.MBMLbMILvs7Uzz-iuagq.xd7v-OCvKwia}
pwn.college{IcF47UuXcc38AuR4tUZHiiHMpNheqhHOwKrLG7ST.eEVdOq}
pwn.college{OXpGAAO4o0lat2ohhFvGqHxgcQRnhJu8v7bKyXnWeSkRWzI}
pwn.college{Ck5vyucg3VPwdY1AoPDGnnDl0Ig92iT8Euw6LQd0GG1G1N7}
pwn.college{lJ26iMPGdxnBeswXtLrpEZsMYVsZAkmuve3Z6kNVqDFfEXq}
pwn.college{Fc4c8ztm-FEY8eh0rAf--McmuyPNfvE.juXy0Ek-bjXpnB-}
pwn.college{zoVoFvSAQJPnuoUBq52QRt3fXY9nGkWaZatHZwALEq-cSXj}
pwn.college{XJQuAJMots2DTQ3ug8vnWTaErGiz0EV5jsrCkKfHYN1w3QK}
pwn.college{jUd2RcGAL4nz3izrEsPPayycPmHFBUc39oxgltx3ei0OPfR}
pwn.college{emkMgytMFx8QCvkzI9WDfG5GkzZzE.twS7EvHxylt491EtK}
pwn.college{jtNgKQuFpEsGisPUnuZOhvXjeMoC7EVVFSohXc6loRvOYE.}
pwn.college{oy3fhYRWnR4hWXydff77Syz17CKfehBR2UYPdflQClwEcjh}
pwn.college{zs8z-Tl7kIjNZ3yg3I8fODfgMlW-PCg7qAPDPPS9nnOLmtu}
pwn.college{30y62oJXBDEkag7dRax6gVe.7WluZfaxtJ1DgeB4jY8gyrO}
pwn.college{hPDc2Pg5.9sktZ8-j16c36I6A4-JxfF38d0vtKZ5vPepMza}
pwn.college{bt5.FUFdico2KKLTFcio9qD73ZGNPyEwGioGTXpV6UiA87c}
pwn.college{xj5PnozE2tGCLas1HkpYz3Bp31UvDtdyblAvnZSgpx7fYgS}
pwn.college{nkb8abha6Xoxs.nb0dZ3K6SULViymU0cNTHiKufB0JG47By}
pwn.college{IeL6fhsWi.zHvI1dVeLPninWLUbk7rfN6KtKKdinlHA31pF}
pwn.college{swP.CSgJlUfagSoesP63akNRrjmsIjRzTRg.Fvc5713S14M}
pwn.college{VmG8o.3.QwuI8l3doXToRoEyTkQv2DJrjueCrnAYQwltQhn}
pwn.college{TJ4N1dsoLq8cRYke0SXJFv9j1vh.KMO83nMAc-NzQ9rFvC1}
pwn.college{-FKUmU70SzPm.YIqbe5alpJ-9MCGjrAntnqMxtQZb7-latI}
pwn.college{I2lxsVuHSfMzstjLyQkSeq4au4xUvEazpmhQmslYR64-mCq}
pwn.college{X55OQ1Irj.WMUoWH9kFmPLqVNebwa9R.XdH83bv.CJgkp7i}
pwn.college{IiUa.ruJUy794ybbJHEqk7iH2HxplCLX8cr.4SIOd1KiyLc}
pwn.college{NKltsIVgBU-.b.L0T7gCJxcJnWsZ8lRRRU0BHU3pJY1ndUs}
pwn.college{fn..6GBcZGA9ty7jZBWKV59jxQDd4uStsGfU0kIziCpncNl}
pwn.college{WdY.OFN1i9fVrA2tSd4ZxkPwei6IbYp2DsOb4jytnIao2KW}
pwn.college{rayNK3SHu8.h0H1eLrBGIIzrDe5bvCXNdBf1VG1uaSqcuev}
pwn.college{ml4YckJByszufv7h7rdKJL1rOFceckZpoQzYShqFtlUMl2q}
pwn.college{-f9E5TRNhs9MfHknlBiOikCfl48ttDR9w4z.cwoebCRSAEa}
pwn.college{ml0FhgHWoeVdbabdRmi0rRc1ziVC.ApEdX5i7XuTdQdFi3v}
pwn.college{QmLW8yMKX5yRda8.MJ6Ewe.nWohsMYF9Sl45pX13ZgPTU0e}
pwn.college{UjURBOCc1GqduDwnlj.U.O3NI-2gjrGMoyD2kFwm8Kuuc1Y}
pwn.college{XQg2u40XcbDmNPe-doUzrVdiMTIjFRLUxqjBB.F4cyEsP58}
pwn.college{jZp0I-W.bD1fdLcoMm1pXhzznWONvM-ezKkK1GpsjB-IZWr}
pwn.college{sJ740xJ.kR6n35ZXnwlCSoyiGjoHpNIzzm2-lx8d9tAJ2vq}
pwn.college{MGEofiyVbNxtiogNnaPyHMGy8-21muiwJ9a.M7zSX0d-H26}
pwn.college{asYLoRWcuR-gv5.TW7F0hN-Xs5gz5homFyft2donEEpmini}
pwn.college{E5XEVhffPrPbRtVf0oi9jQq-BonV2p.7I7FPy6RJ4jUa9Hz}
pwn.college{sNOt9FCcPddt.62jFaNoBWOLALCjWmUAO2c9av0YZP0Q-pY}
pwn.college{h4LjT3N1-yzZum.s-qI7AQqVuDF0gY75hpjLjR3MuSMFkJG}
pwn.college{kpNs-tqPAxigIqol.kuzWcLk1Q67lk2xPvQeg.rx4AMIKG.}
pwn.college{cjwjJbXEC.seZx2uJ8XNmo8uHbGmT5DOHftFU8jG6ksbZZw}
pwn.college{kjRIdRfOupiqJGLUq-Rc7CUoUJ6EzDm5yC0wlyp7NY2JknI}
pwn.college{tcKAMNf.S6YkIUVSyZQEx-3Ptg6cT7jM3ASpzZN8PyBOWFE}
pwn.college{l1fJto7RU26H9nYIU7QUIKC-WyNwcyeH7UhxW61CfM2j1Y6}
pwn.college{9HX8onZBBFO2WrpODB-l6.mOmiYGHpmhXtTlIMSJSPzpl7J}
pwn.college{xQBFEWFOlZG0fVti0nt.XAhPrQ4ai3mP2qeeLFAezLCN2zx}
pwn.college{VKt8KDnqLLcrB0ZlXuh-mFX0dwY0xpVL2cXzytGf-9uVOqL}
pwn.college{M8Yq6NPBUvGdZi53CEEaZPTnKlr.0FNzMDOxwSNxIzNzEzW}
pwn.college{M8Yq6NPBUvGdZi53CEEaZPTnKlr.0FNzMDOxwSNxIzNzEzW}










hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         153     144  0 14:07 pts/1    00:00:00 bash /challenge/run
root         155     153  0 14:07 pts/1    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         153     144  0 14:07 pts/1    00:00:00 bash /challenge/run
root         160     144  0 14:07 pts/1    00:00:00 bash /challenge/run
root         162     160  0 14:07 pts/1    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{UYMDQb2CiKyfs71OMDSz2TNl581.QX1QDO0wSNxIzNzEzW}




hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         220     197  0 14:13 pts/3    00:00:00 bash /challenge/run
root         222     220  0 14:13 pts/3    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ fg
/challenge/run

hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         220     197  0 14:13 pts/3    00:00:00 bash /challenge/run
root         222     220  0 14:13 pts/3    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         220     197  0 14:13 pts/3    00:00:00 bash /challenge/run
root         229     197  0 14:16 pts/3    00:00:00 bash /challenge/run
root         231     229  0 14:16 pts/3    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{UYMDQb2CiKyfs71OMDSz2TNl581.QX1QDO0wSNxIzNzEzW}








hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ jobs
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
fg
Goodbye!
hacker@processes~resuming-processes:~$ jobs
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg %1
/challenge/run
I'm back! Here's your flag:
pwn.college{EjndReypc857xtOi5Hi-a-a4Yjv.QX2QDO0wSNxIzNzEzW}
Don't forget to press Enter to quit me!




hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         159 S+   bash /challenge/run
root         161 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         159 S    bash /challenge/run
root         169 S    sleep 6h
root         172 S+   bash /challenge/run
root         174 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{U2KxSDmdzTWneAsSmxFXU6vauNw.QX3QDO0wSNxIzNzEzW}





hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{k4cnhm52f8Wic_YcvY8lwYRgka5.QX4QDO0wSNxIzNzEzW}






hacker@processes~starting-backgrounded-processes:~$ /challenge/run
You've started me in the foreground! You must start me in the background (by 
appending '&' to the command) to get the flag!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 141
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{EqlAVoeQzPIM9mkepJ8dcbN4oQQ.QX5QDO0wSNxIzNzEzW}






hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ /challenge/submit-code $?
CORRECT! Here is your flag:
pwn.college{Y7uWd8TsIKBk9cZk6pP2rjGaoux.QX5YDO1wSNxIzNzEzW}














