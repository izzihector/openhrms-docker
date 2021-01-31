FROM nikolaik/python-nodejs:python3.9-nodejs15


RUN apt-get update && apt-get install git

RUN adduser --system --home=/opt/openhrms --group openhrms \
  && mkdir /var/log/openhrms

RUN git clone https://www.github.com/odoo/odoo.git --depth 1 --branch 11.0 --single-branch /opt/openhrms \
  && git clone https://github.com/CybroOdoo/OpenHRMS.git --depth 1 --branch 11.0 --single-branch /opt/openhrms/openhrms

RUN -H pip3 install --upgrade pip \
  && -H pip3 install -r /opt/openhrms/doc/requirements.txt \
  && -H pip3 install -r /opt/openhrms/requirements.txt \
  && pip3 install pandas \
  && curl -sL https://deb.nodesource.com/setup_6.x | -E bash -

RUN npm install -g less less-plugin-clean-css

RUN cd /tmp \
  && wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.4/wkhtmltox-0.12.4_linux-generic-amd64.tar.xz \
  && tar -xvf wkhtmltox-0.12.4_linux-generic-amd64.tar.xz

RUN mv wkhtmltox/bin/wk* /usr/bin/ \
    && chmod a+x /usr/bin/wk