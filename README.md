video :https://drive.google.com/file/d/130zutAUA9E55rpRAY9_rBEvDPAM6O2cJ/view?usp=drive_link



//code for  AmountDistributionHandler

public class AmountDistributionHandler { 
    public static void amountDist(list<Appointment__c> listApp){ 
        list<Service_records__c> serList = new list <Service_records__c>(); 
        for(Appointment__c app : listApp){ 
            if(app.Maintenance_service__c == true && app.Repairs__c == true && 
app.Replacement_Parts__c == true){ 
                app.Service_Amount__c = 10000; 
            } 
            else if(app.Maintenance_service__c == true && app.Repairs__c == true){ 
                app.Service_Amount__c = 5000;     
            } 
            else if(app.Maintenance_service__c == true && app.Replacement_Parts__c == true){ 
                app.Service_Amount__c = 8000;     
            } 
            else if(app.Repairs__c == true && app.Replacement_Parts__c == true){ 
                app.Service_Amount__c = 7000; 
            } 
            else if(app.Maintenance_service__c == true){ 
                app.Service_Amount__c = 2000; 
            } 
            else if(app.Repairs__c == true){ 
                app.Service_Amount__c = 3000; 
            } 
            else if(app.Replacement_Parts__c == true){ 
                app.Service_Amount__c = 5000; 
            }            
    } 
    } 
}




//code for AmountDistribution
 
trigger AmountDistribution on Appointment__c (before insert, before update) { 
if(trigger.isbefore && trigger.isinsert || trigger.isupdate){ 
AmountDistributionHandler.amountDist(trigger.new); 
} 
}
