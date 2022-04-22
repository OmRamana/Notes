# Notes
Making queries to django models

Create action in the django rest framework viewset

from django.dispatch import receiver
from django.db.models.signals import post_save
from django.core.mail import EmailMultiAlternatives

from django.http import JsonResponse
from django.forms.models import model_to_dict

    @action(methods=['get'], detail=False)
    def confirm_appointment(self,request):
        pk = request.query_params['pk']
        appointment = Appointment.objects.get(pk=pk)
        appointment.is_confirmed = True
        #appointment.status = "Confirmed"
        appointment.save()
        return JsonResponse(model_to_dict(appointment))



Send email on Model creation django
     
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

  
