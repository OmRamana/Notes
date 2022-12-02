Microsoft Windows [Version 10.0.22621.819]
(c) Microsoft Corporation. All rights reserved.

C:\Users\keanu\Documents\anatomy_2>echo "# anatomy_2" >> README.md

C:\Users\keanu\Documents\anatomy_2>git init
Initialized empty Git repository in C:/Users/keanu/Documents/anatomy_2/.git/

C:\Users\keanu\Documents\anatomy_2>git add README.md

C:\Users\keanu\Documents\anatomy_2>git add water_drinking_pattern.png

C:\Users\keanu\Documents\anatomy_2>git commit -m "first commit"
[master (root-commit) 674491c] first commit
 2 files changed, 1 insertion(+)
 create mode 100644 README.md
 create mode 100644 water_drinking_pattern.png

C:\Users\keanu\Documents\anatomy_2>git branch -M main

C:\Users\keanu\Documents\anatomy_2>git remote add origin https://github.com/OmRamana/anatomy_2.git

C:\Users\keanu\Documents\anatomy_2>git push -u origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 36.63 KiB | 7.33 MiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/OmRamana/anatomy_2.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.

C:\Users\keanu\Documents\anatomy_2>





React tuts
https://www.youtube.com/watch?v=CXa0f4-dWi4
https://www.youtube.com/watch?v=fL8cFqhTHwA
https://www.youtube.com/watch?v=3nLTB_E6XAM


cmd in the current directory;
Once you’re in the right folder, click on the address bar at the top and simply type in cmd and press Enter

Changes made to the github repo online, command line push method;
git pull origin master,
git push origin master

View git remote; git remote -v

Change git remote; git remote set-url <remote_name> <remote_url> eg git remote set-url origin https://git-repo/new-repository.git

Run a cloned react app; $ npm install; $ npm start

Json Reading; Json single quoted, paste it in vs code and highlight a single quote, right click , select all occurrences , change it into double quote, right click and format the document
**Email sending and model updates django rest framework**

```from django.dispatch import receiver
from django.db.models.signals import post_save
from django.core.mail import EmailMultiAlternatives
from django.http import JsonResponse
from django.forms.models import model_to_dict

#update model fields based on request params

    @action(methods=['get'], detail=False)
    def confirm_appointment(self,request):
        pk = request.query_params['pk']
        appointment = Appointment.objects.get(pk=pk)
        appointment.is_confirmed = True
        #appointment.status = "Confirmed"
        appointment.save()
        return JsonResponse(model_to_dict(appointment))

#Send email on Model creation django
     
     @receiver(post_save, sender=Appointment)
     def send_appointment_request_mail(sender, instance, created, **kwargs):
       if not created:
          return
       subject, from_email, to , pk = 'Appointment Request', 'TelePsycRX@telepsycrx.com', instance.patient.email, instance.id
       text_content = 'You have an appointment request.'  
       doc = instance.doctor.first_name
       html_content = f'<p>You have an appointment request from Doctor {doc}</p><a href="http://127.0.0.1:8000/api/accounts/appointments/confirm_appointment/?pk=' +    str(pk) + '">Confirm </a>'
       msg = EmailMultiAlternatives(subject, text_content, from_email, [to])
       msg.attach_alternative(html_content, "text/html")
       msg.send()

#Send an email after model update django

@receiver(post_save, sender=Appointment)
def send_appointment_reschedule_email(sender, instance, raw, created, **kwargs):
    if created or raw:
        return
    #stuff after model creation    
    subject, from_email, to , pk = 'Appointment Reschedule', 'TelePsycRX@telepsycrx.com', instance.doctor.email, instance.id
