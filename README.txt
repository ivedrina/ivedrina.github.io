Ishod 1: Mogucnosti sustava otvorenog koda, paketni sustavi
	- RH124: Poglavlja 2 - 5,12
Ishod 2: Konfiguracija korisnika, grupa, diskovnog prostora i osnovnih servisa
	- RH124: Poglavlja 6,7,13
	- RH134: Poglavlja 7
Ishod 3: Konfiguracija mehanizama za pohranu zapisa o radu sustava 
	- RH124: Poglavlje 10
	- RH134: Poglavlja 2,3
Ishod 4: Konfiguracija mreznih servisa
	- RH124: Poglavlje 11
Ishod 5: Konfiguracija sustava za upravljanje mreznim adresama i email
	- RH254: Poglavlja 5,6 + vjezbe sa Infoeduke
Ishod 6: Sustavi za isporuku web-stranica
	- RH254: Poglavlje 10 + vjezba sa Infoeduke


su - *noviuser* (switch user)
passwd 
file *putanja datoteke*  -provjera tipa datotekefile 
head -n 3
tail -n 3
wc -l(-w, -c) *putanja datoteke* 	-counts lines, words, and characters in a file
date +%R(A,M,S,...)

mkdir -p *putanja datoteke* (naredba stvara i ostale direktorije koje ne postoje još na putanji)

touch song{1..6}.mp3

cp -r ~/family ~/friends . (kopiraj cijeli family i friends direktorij u trenutačni direcd ..(to predstavlja .)
cp imedatoteke.jpg imedatoteke_$(date +%F).jpg (kopira datoteku i u naziv nove dat dodaje date)


ln newfile.txt /tmp/newfile-hlink2.txt (hard link)
ln -s newfile-link2.txt /tmp/newfile-symlink.txt


echo ~/*ime datoteke ili direktorija*  (putanja od home direk do navedene datoteke ili direk)


$ var=40
$ echo var 
var

$ echo $var 
40

dnf info		dnf group info "naziv grupe"
dnf search
dnf install 		dnf group install "naziv grupe"
dnf list
dnf remove 
dnf history
dnf history info 3
dnf history undo 3


dnf repolist all
dnf config-manager --enable *naziv repozetorija*
dnf config-manager --disable *naziv repozetorija*
dnf config-manager --add-repo="https://*repzetorij*/"


echo "------------" >> $lab_file

echo $HOME (user's home directory)
echo $PATH (locations of the user's executable files)

useradd *ime usera*
tail /etc/passwd 	(provjera dali user postoji)
passwd  *ime usera*
userdel -r *ime usera*
ls -la /home 	(provjera dali postoji home direktorij od usera)

usermod -c "*zapis commenta*" *ime usera*
usermod -aG *naziv grupe* *ime usera* (dodavanje usera u grupu)

useradd -G *naziv grupe* *ime usera* (dodavanje novog usera u grupu)

groupadd *naziv grupe*
groupadd -g 10000 *naziv grupe*
cat /etc/group (provjera postojećih grupa)

chage -l *ime usera* (status lozinke za usera)
chage -d 0 *ime usera* (users must change the password when they first log in)



echo "%admin ALL=(ALL) ALL" >> /etc/sudoers.d/admin (members of the admin group have full administrative privileges)

vim /etc/login.defs (newly created users must change their passwords every 30 days)

chmod g+(ili-)w  *ime direktorija ili filea*
chmod 770 /home/consultants  (Forbid others from accessing file)

chmod 2770 /home/consultants (dodavanje specijalnih premisija -prvi broj)
chmod 0770 /home/consultants (oduzimanje specijalnih premisija)"

chown *ime usera* *ime datoteke ili direk*
chown :*ime grupe* *ime datoteke ili direk*

umask 027 (promjena umaska za tog usera na br 027, gubi se nakon log outa)

echo "umask 007" >> ~/.bashrc (trajna promjena, ne gubi se nakon log outa)


du /usr/share > /mnt/freespace/results.txt (zapis naredbe - Generate a disk usage report u text file)

parted /dev/vdb print (inspekcija particije)
lsblk --fs /dev/vdb (UUID broj)


nmtui (network manager tui)
sudopokrenuti kao root
kad se aktivira konekcija ostaje aktivna nakon reboota
- kad se dodaje address2 mora se :
	nmcli con reload
	nmcli con up "naziv konekcije" 


 -r  *ime servisa* (restartanje servisa)
systemctl restart dnsmasq (nakon izmjene /etc/dnsmasq.conf i /etc/hosts)
systemctl status dnsmasq
netstat -tulnp (provjera jel  se dnsmasq bindao na pravi port)

dnsmasq
-----
domain -needed
bogus -priv
no -resolv
interface=eth0
expand-hosts
domain=*mikro.local*
----
**za mail -dodatak
listen address=172.25.250.11
mx-host=mikro.local, mail.mikro.local, 10
----- 

dnf install bind
systemctl restart named
systemctl status named
*slika s vjezba


email
--------
vim /etc/postfix/main.cf

myhostname=mail.mikro.local
mydomain=mikro.local
myorigin=$mydomain
inet_interfaces=all
inet_protocols=all
mydestination=________ ,$mydomain(dodati)
mynetworks= 127.0.0.0/8, 172.25.250.0/24(dodati potrebnu)
mail_spool_dirctory= /var/spool/mail
------

provjera prije rebootanja
sudo mount -rav

sudo dnf list --installed | grep httpd (provjera dali je program instalirani)

mkdir -p Racunovodstvo/{Sij,Vel,Ozu}/Fakture/{Izlazne,Ulazne}/{Obrada,Obradeno,Priprema}

touch Racunovodstvo/{Sij,Vel,Ozu}/Fakture/{Izlazne,Ulazne}/{Obrada,Obradeno,Priprema}/popis-faktura.txt


sudo dnf config-manager --add-repo "http://content.example.com/rhel9.0/x86_64/rhcsa-practice/rht"
dnf repolist all
sudo vim /etc/yum.repos.d/content.example.com_rhel9.0_x86_64_rhcsa-practice_rht.repo
gpgcheck=0
dnf install 

sudo adduser **
sudo su - **
ssh -keygen
ssh-copy-id student@serverb
yes
ssh student@serverb








Dimension by HTML5 UP
html5up.net | @ajlkn
Free for personal and commercial use under the CCA 3.0 license (html5up.net/license)


This is Dimension, a fun little one-pager with modal-ized (is that a word?) "pages"
and a cool depth effect (click on a menu item to see what I mean). Simple, fully
responsive, and kitted out with all the usual pre-styled elements you'd expect.
Hope you dig it :)

Demo images* courtesy of Unsplash, a radtastic collection of CC0 (public domain) images
you can use for pretty much whatever.

(* = not included)

AJ
aj@lkn.io | @ajlkn


Credits:

	Demo Images:
		Unsplash (unsplash.com)

	Icons:
		Font Awesome (fontawesome.io)

	Other:
		jQuery (jquery.com)
		Responsive Tools (github.com/ajlkn/responsive-tools)
