#include <iostream>
#include <string.h>
#include <vector>
#include <cstring>
#include <iomanip>
#include<math.h>
#include<complex>


using namespace std;

class Polynomial {
protected:
    vector<double> mCoeffs;
    uint32_t mDegree;
public:
    Polynomial(const vector<double> &v) {
        mCoeffs = v;
        mDegree = v.size() - 1;

    }

    Polynomial(uint32_t x) {
        for (int i = 0; i < x + 1; i++) {
            mCoeffs.push_back(0);
        }
        mDegree = x;
    }

    Polynomial derivate() const {
        Polynomial poli(mDegree - 1);

        for (int i = 0; i < poli.mCoeffs.size(); i++) {
            poli.mCoeffs[i] = mCoeffs[i] * (mDegree - i);
        }
        return poli;

    }

    double calculate(double value) const {
        double rez;
        for (int i = 0; i < mCoeffs.size(); i++) {
            rez = rez + pow(value, mDegree - i) * mCoeffs[i];
        }
        return rez;
    }

    uint32_t getDegree() const {
        return mDegree;
    }

    double &operator[](uint32_t index) {
        return mCoeffs[index];
    }

    double operator[](uint32_t index) const {
        return mCoeffs[index];
    }

    Polynomial operator+(const Polynomial &rhs) const {
        uint32_t x;
        if (rhs.mDegree < mDegree)
            x = mDegree;
        else x = rhs.mDegree;
        uint32_t dif;


        if (rhs.mDegree < mDegree) {
            dif = mDegree - rhs.mDegree;
            Polynomial sumica(mDegree);
            int i = dif;
            int j = 0;
            while (i <= mDegree && j <= rhs.mDegree) {
                sumica.mCoeffs[i] = mCoeffs[i] + rhs.mCoeffs[j];
                i++;
                j++;
            }
            for (int i = 0; i < dif; i++)
                sumica.mCoeffs[i] = mCoeffs[i];
            return sumica;
        }
        if (rhs.mDegree > mDegree) {
            dif = rhs.mDegree -mDegree;
            Polynomial sumica(rhs.mDegree);
            int j = dif;
            int i = 0;
            while (j <=rhs.mDegree && i <= mDegree) {
                sumica.mCoeffs[j] = mCoeffs[i] + rhs.mCoeffs[j];
                i++;
                j++;
            }
            for (int i = 0; i < dif; i++)
                sumica.mCoeffs[i] = rhs.mCoeffs[i];
            return sumica;
        }
    }
    Polynomial operator*(const Polynomial& rhs) const
    {Polynomial prod(mDegree+rhs.mDegree);
        for(int i=0; i<mCoeffs.size(); i++)
        {
            for(int j=0; j<rhs.mCoeffs.size(); j++)
            {
                prod.mCoeffs[i+j]+=mCoeffs[i]*rhs.mCoeffs[j];
            }

        }
        return prod;
    }
    std::complex<double> calculate(const std::complex<double>& value) const
    {
        return value;
    }
    void print() {
        for (int i = 0; i < mCoeffs.size(); i++) {
            cout << mCoeffs[i] << " ";
        }
    }
    Polynomial& operator*=(const double constant)
    {for(int i=0;  i<mCoeffs.size(); i++)
        {
            mCoeffs[i]=mCoeffs[i]*constant;

        }
        return *this;

    }
    Polynomial& operator/=(const double constant)
    {for(int i=0;  i<mCoeffs.size(); i++)
        {
            mCoeffs[i]=mCoeffs[i]/constant;

        }
        return *this;
    }
    virtual std::vector<std::complex<double>> roots() const
    {
        vector<complex<double>>v;


    return v;
    }



};
class ZeroDegreePolynomial:public Polynomial
{
    ZeroDegreePolynomial(const vector <double> &v ):Polynomial(v)
    {
    }
    std::vector<std::complex<double>> roots() const
    {
        cout<<"Polynomials with degree 0 doesn't have roots.\n";
          vector<complex<double>>v;
          return v;

    }
};
class FirstDegreePolynomial:public Polynomial
{
    FirstDegreePolynomial(const vector <double> &v ):Polynomial(v)
    {}
    std::vector<std::complex<double>> roots() const
    {
        double x;
        x=(-mCoeffs[1])/mCoeffs[0];
        vector<complex<double>>v;
        complex<double>ve(x,0);
        v.push_back(ve);
        return  v;


    }
};
class SecondDegreePolynomial:public Polynomial
{
    SecondDegreePolynomial(const vector<double> &v): Polynomial(v)
    {}
    std::vector<std::complex<double>> roots() const
    {
        double x1,delta, x2;
        delta=mCoeffs[1]*mCoeffs[1]-4*mCoeffs[0]*mCoeffs[1];
        if(delta>0) {
            x1 = (-mCoeffs[1] + sqrt(delta))/(2*mCoeffs[0]);
            x2=(-mCoeffs[1] - sqrt(delta))/(2*mCoeffs[0]);
            vector<complex<double>>v;
            complex<double>ve1(x1,0);
            complex<double>ve2(x2,0);
            v.push_back(ve1);
            v.push_back(ve2);
            return  v;


        }
        if(delta==0)
        {
            x1=(-mCoeffs[1])/(2*mCoeffs[0]);
            vector<complex<double>>v;
            complex<double>ve1(x1,0);
            v.push_back(ve1);
            return  v;
        }
        if(delta<0)
        {
            x1=(-mCoeffs[1]/(2*mCoeffs[0]));
            vector<complex<double>>v;
            complex<double>ve1(x1,sqrt(-delta)/(2*mCoeffs[0]));
            complex<double>ve2(x1,-sqrt(-delta)/(2*mCoeffs[0]));
            v.push_back(ve1);
            v.push_back(ve2);
            return  v;
        }
    }


};


int main() {
 int n;
 cin>>n;
 cin.get();
 vector<Polynomial> polinomite;
 for(int i=0; i<n; i++)
 {
     char s[500];
     vector<double> coeficientei;
     cin.getline(s,500);
     char *p= strtok(s," ");
     while(p!=NULL)
     {
         double x= stoi(p);
         coeficientei.push_back(x);
         p= strtok(NULL, " ");

     }
     Polynomial coef(coeficientei);
     polinomite.push_back(coef);
 }
 string cerinta;
 while(cin>>cerinta)
 {if(cerinta=="div")
     {
     double index, real;
     cin>>index>>real;
     polinomite[index]=polinomite[index].operator/=(real);
     }
     if(cerinta=="add")
     {
         double index1, index2, index;
         cin>>index1>>index2>>index;
         polinomite[index]=polinomite[index1].operator+(polinomite[index2]);
     }
     if(cerinta=="mult")
     {
         int index, index1, index2;


         cin>>index;
         cin>>index1;
         if(getchar()==' ')
         {cin>>index2;
             polinomite[index]=polinomite[index1].operator*(polinomite[index2]);

         }
         else {   polinomite[index]=polinomite[index1].operator*=(index1);


         }
     }

 }
 return 0;

}
