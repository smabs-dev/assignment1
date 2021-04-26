// AccountHolder.java
package com.meritamerica.assignment1;

public class AccountHolder {
	//instance variables
	
	private String firstName;
	private String middleName; 
	private String lastName;
	private String ssn;
	private double checkingAccountOpeningBalance;
	private double savingsAccountOpeningBalance;
	private CheckingAccount checking;
	private SavingsAccount savings;
	
  // default constructor
public AccountHolder(){
}
  // special constructor
public AccountHolder(
		String firstName, 
		String middleName, 
		String lastName,
		String ssn,
		double checkingBal,
		double savingsBal)
{
	this.firstName= firstName;
	this.middleName= middleName;
	this.lastName= lastName;
	this.ssn= ssn;
	this.checkingAccountOpeningBalance= checkingBal;
	this.savingsAccountOpeningBalance= savingsBal;
	this.checking= new CheckingAccount(checkingBal);
	this.savings= new SavingsAccount(savingsBal);
	
}

//getter setter methods


public String getMiddleName() {
	return middleName;
}
public CheckingAccount getCheckingAccount() {
	return checking;
}
public SavingsAccount getSavingsAccount() {
	return savings;
}
public String getFirstName() {
	return firstName;
}
public void setFirstName(String firstName) {
	this.firstName = firstName;
}
public void setMiddleName(String middleName) {
	this.middleName = middleName;
}
public String getLastName() {
	return lastName;
}
public void setLastName(String lastName) {
	this.lastName = lastName;
}
public String getSsn() {
	return ssn;
}
public void setSsn(String ssn) {
	this.ssn = ssn;
}
public double getCheckingAccountOpeningBalance() {
	return checkingAccountOpeningBalance;
}
public void setCheckingAccountOpeningBalance(double checkingAccountOpeningBalance) {
	this.checkingAccountOpeningBalance = checkingAccountOpeningBalance;
}
public double getSavingsAccountOpeningBalance() {
	return savingsAccountOpeningBalance;
}
public void setSavingsAccountOpeningBalance(double savingsAccountOpeningBalance) {
	this.savingsAccountOpeningBalance = savingsAccountOpeningBalance;
}
@Override
public String toString() {
	return "AccountHolder [firstName=" + firstName + ", middleName=" + middleName + ", lastName=" + lastName + ", ssn="
			+ ssn + ", checkingAccountOpeningBalance=" + checkingAccountOpeningBalance
			+ ", savingsAccountOpeningBalance=" + savingsAccountOpeningBalance + "]";
}
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
//CheckingAccount.java

package com.meritamerica.assignment1;
//This is the template for a new Checking Account
public class CheckingAccount {
	
	private double balance;
	private double interestRate = 0.0001;

	public CheckingAccount(double balance) {
		super();
		this.balance = balance;
	}

	public double getBalance() {
		return balance;
	}

	public double getInterestRate() {
		return interestRate;
	}

	public double futureValue(int years) {
		double factor = 1+interestRate;
		return Math.pow(factor, years) * balance;
	}
	//	FV=balance * (1+i) ^n;
	public boolean withdraw (double amount) {
	if (amount<balance) {
		System.out.println(balance-amount);
		balance = balance - amount;
		return true;
	}
	else
		return false;
	}
	
	public boolean deposit (double amount)
	{
	if (amount>0) {
		System.out.println(balance+amount);
		balance = balance + amount;
		return true;
	}
	else
		return false;
	}

	@Override
	public String toString() {
		return "CheckingAccount [balance=" + balance + ", Interest Rate=" + interestRate + "Future Value = "
				+ futureValue(3) +"]";
	}
}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
//SavingsAccount.java

package com.meritamerica.assignment1;
// This is the template for a new Savings Account
public class SavingsAccount {
	private double balance;
	private double interestRate = 0.01;

	public SavingsAccount(double balance) {
		super();
		this.balance = balance;
	}
	public double getBalance() {
		return balance;
	}
	public double getInterestRate() {
		return interestRate;
	}
	public double futureValue(int years) {
		double factor = 1+interestRate;
		return Math.pow(factor, years) * balance;
	}

	public boolean withdraw (double amount) {
	if (amount<balance) {
		System.out.println(balance);
		balance = balance - amount;
		return true;
	}
	else
		return false;
	}
	public boolean deposit (double amount)
	{
	if (amount>0) {
		System.out.println(balance+amount);
		balance = balance + amount;
		return true;
	}
	else
		return false;
	}
//to string
	@Override
	public String toString() {
		return "SavingsAccount [balance=" + balance + ", interestRate=" + interestRate + "]";
	}
}
/*
 * SavingsAccount(double openingBalance)
double getBalance()
double getInterestRate()
boolean withdraw(double amount)
boolean deposit(double amount)
double futureValue(int years)
String toString()
Sample output:
Savings Account Balance: $1000
Savings Account Interest Rate: 0.01
Savings Account Balance in 3 years: $1030.03

 */
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
//MeritAmericaBankApp.java

package com.meritamerica.assignment1;

public class MeritAmericaBankApp {

	public static void main(String[] args) {

AccountHolder actHolderRahmanJ= new AccountHolder("Rahman", " ", "Jones", "123456789", 100.0, 1000.0);
System.out.println(actHolderRahmanJ);
actHolderRahmanJ.getCheckingAccount().deposit(500.00);
actHolderRahmanJ.getSavingsAccount().withdraw(800.00);
System.out.println(actHolderRahmanJ.getCheckingAccount().toString());
System.out.println(actHolderRahmanJ.getSavingsAccount().toString());
AccountHolder actHolderBillB = new AccountHolder("Bill", " ", "Belemy", "23456891", 200.0, 500.0);
System.out.println(actHolderBillB);
actHolderBillB.getCheckingAccount().deposit(-500.00);
actHolderBillB.getSavingsAccount().withdraw(600.00);
System.out.println(actHolderBillB.getCheckingAccount().toString());
System.out.println(actHolderBillB.getSavingsAccount().toString());
	}
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
SolutionTest.java
Runs 9/9
Errors: 0
Failures: 0
