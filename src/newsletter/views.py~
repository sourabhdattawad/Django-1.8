from django.shortcuts import render
from django.core.mail import send_mail
from .forms import ContactForm, SignUpForm
from django.conf import settings
# Create your views here.
def home(request):
	title = "Welcome"
	form = SignUpForm(request.POST or None)
	context={
		"title":title,
		"form":form

	}
	
	if form.is_valid():
		instance = form.save(commit=False)
		instance.save()
		context={
		"title": "Thank You"
		}
	
	return render(request, "home.html", context)

def contact(request):
	title = 'Contact Us'
	title_align_center = True
	form = ContactForm(request.POST or None)
	if form.is_valid():
		# for key, value in form.cleaned_data.iteritems():
		# 	print key, value
		# 	#print form.cleaned_data.get(key)
		form_email = form.cleaned_data.get("email")
		form_message = form.cleaned_data.get("message")
		form_full_name = form.cleaned_data.get("full_name")
		# print email, message, full_name
		subject = 'Site contact form'
		from_email = settings.EMAIL_HOST_USER
		to_email = [from_email, 'yourotheremail@gmail.com']
		contact_message = "%s: %s via %s"%( 
				form_full_name, 
				form_message, 
				form_email)
		some_html_message = """
		<h1>hello</h1>
		"""
		send_mail(subject, 
				contact_message, 
				from_email, 
				to_email, 
				html_message=contact_message,
				fail_silently=True)



		c_email = [from_email, form_email]
		c_message = "Thank You. I'll get back to you soon."
		
		send_mail(subject, 
				c_message, 
				from_email, 
				c_email, 
				html_message=c_message,
				fail_silently=True)




		

	context = {
		"form": form,
		"title": title,
		"title_align_center": title_align_center,
	}
	return render(request, "contact.html", context)


def project(request):
	return render(request, "project.html")













