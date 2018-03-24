# Deploying django application on EBS

Deplying sample django application on EBS-Elastic Beanstalk

1. To deploy Django on EBS we need to install awsebcli
            
       pip install awsebcli



2. Create a virtual environment named eb-virt.

       virtualenv ~/eb-virt

3. Activate the virtual environment.

       source ~/eb-virt/bin/activate

4. Install django

       (eb-virt)~$  pip install django==1.9.12

5. Creating django project

       (eb-virt)~$ django-admin startproject ebdjango

6. Running Django site locally with manage.py runserver:

        (eb-virt) ~$  cd ebdjango
        (eb-virt) ~/ebdjango$  python manage.py runserver


7. Open http://127.0.0.1:8000/ in a web browser to view the site:



8. Configuring to EBS

       (eb-virt) ~/ebdjango$  source ~/eb-virt/bin/activate
       (eb-virt) ~/ebdjango$  pip freeze > requirements.txt
       (eb-virt) ~/ebdjango$ mkdir .ebextensions
       (eb-virt) ~/ebdjango$ cd .ebextensions

       (eb-virt) ~/ebdjango$ vi django.config

    Add the following to the file:

                  option_settings:
                    aws:elasticbeanstalk:container:python:
                      WSGIPath: ebdjango/wsgi.py

9. creating project in eb:

       ~/ebdjango$ eb init -p python-2.7 django-tutorial
       ~/ebdjango$ eb create django-env
       ~/ebdjango$ eb open


Step -1.9: This will open a browser window using the domain name created for your application. You should see the same Django website that you created and tested locally.

Sample Django application is deployed on EBS successfully.



