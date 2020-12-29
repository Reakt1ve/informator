<h1><b>Fpmail</b></h1>

<p>This docker image will run as a single process.</p>

<h2>Volume</h2>
<p>Run as a single container:</p>
<pre>docker run --rm -d \
            -v /etc/fpmail/.procmailrc:/home/fetchmail/.procmailrc \ 
            -v /etc/fpmail/fetchmail:/home/fetchmail/fetchmailrc \
            -v /etc/fpmail/procmailrc:/home/fetchmail/procmailrc \
            -v /etc/fpmail/Mail:/home/fetchmail/Mail \
            -e FPMAIL_OUT_DMS="172.16.120.14" fpmail
</pre>
<p>Note: FPMAIL_OUT_DMS is optional env variable. It is required in case if you have a decision-making system.</p>

<h2>Docker-compose</h2>
<pre>fpmail:
         image: fpmail:latest
         restart: always
         environment:
           FPMAIL_OUT_DMS
         volumes:
           - /etc/fpmail/.procmailrc:/home/fetchmail/.procmailrc
           - /etc/fpmail/fetchmailrc:/home/fetchmail/fetchmailrc
           - /etc/fpmail/procmailrc:/home/fetchmail/procmailrc
           - /etc/fpmail/Mail:/home/fetchmail/Mail
         ports:
           - 993:993
           - 10128:10128
</pre>
