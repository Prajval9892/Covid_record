# Covid_record
this project going to maintain the number of record of covid patient .
import re
class covid_19:
    def __init__(self):
        self.date=[]
        self.day_case=[]
        self.total_number_of_case=[]
        self.day_death=[]
        self.total_death=[]
        self.total_recover=[]
        self.day_recover=[]
        self.total_active=[]
        self.ttotal_recover=0
        self.ttotal_number_of_case=0
        self.ttotal_death=0
        self.flag=1
    def update_info(self):
        date=input("Enter date in dd/mm/yy formate")
        date_re=re.compile(r'\d+/{1}\d+/{1}\d+')
        self.flag=date_re.findall(date)
        if len(self.flag)==0:
            print("please enter date valid formate dd/mm/yy")
        else:
            self.date.append(date)
            
            day_case=input("Enter todays number of case")
            self.ttotal_number_of_case=int(day_case)+int(self.ttotal_number_of_case)
            self.day_case.append(day_case)
            self.total_number_of_case.append(self.ttotal_number_of_case)
                
            day_death=input("Enter todays death")
            
            self.ttotal_death=int(self.ttotal_death)+int(day_death)
            self.day_death.append(day_death)
            self.total_death.append(self.ttotal_death)
                    
            day_recover=input("Enter todays recover")
            self.ttotal_recover=int(day_recover)+int(self.ttotal_recover)
            total_active=int(self.ttotal_number_of_case)-int(self.ttotal_recover)-int(day_death)
            self.day_recover.append(day_recover)
            self.total_recover.append(self.ttotal_recover)
            self.total_active.append(total_active)

    def print_info(self):
        print("Todays case==>",self.day_case)
        print("total case==>",self.total_number_of_case)
        print("today death==>",self.day_death)
        print("today recover",self.day_recover)
        print("total recover==>",self.total_recover)
        print("Total Active case==>",self.total_active)
    @classmethod
    def update_veriable(cls,self,day_case,total_number_of_case,day_death,total_death,total_recover,day_recover,total_active):
        cls.day_case=self.day_case
        cls.total_number_of_case=self.total_number_of_case
        cls.day_death=self.day_death
        cls.total_death=self.total_death
        cls.total_recover=self.total_recover
        cls.day_recover=self.day_recover
        cls.total_active=self.total_active
        cls.ttotal_recover=self.ttotal_recover
        cls.total_number_of_case=self.ttotal_number_of_case
        cls.ttotal_death=self.ttotal_death
class covid_case(covid_19):
                   pass


c=covid_19()

c.update_info()


from tabulate import tabulate
print("<==============================================COVID CONDITION IN INDIA===============================================>")
col_span=10
print("="*118)
li=["Date","Today Case","Today Recover","Today Death","Total recover","Total Death","Total Acive","Total Case"]
my={"Date":c.date,"Today case":c.day_case,"Today Recover":c.day_recover,"Today death":c.day_death,"Total recover":c.total_recover,"Total death":c.total_death,"Total Active":c.total_active,"Total Case":c.total_number_of_case}
print(tabulate(my,headers=li))



