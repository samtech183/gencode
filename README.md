#include<bits/stdc++.h>
using namespace std;
typedef long long ll;
typedef pair<long long,long long> pll;
typedef vector<long long> vll;
#define pb push_back
#define all(a) (a).begin(), (a).end()
#define fi first
#define se second
#define mp make_pair
#define Mid ((left+right)/2)
#define flash ios_base::sync_with_stdio(false);cin.tie(0);cout.tie(0)

void convert(ll value,string &s){
	string ones[20]={"Zero", "One", "Two", "Three","Four","Five","Six","Seven","Eight","Nine","Ten","Eleven","Twelve","Thirteen","Fourteen","Fifteen","Sixteen","Seventeen",
    "Eighteen","Nineteen"};
    string tens[10] = {"", "Ten", "Twenty", "Thirty","Forty","Fifty","Sixty","Seventy","Eighty","Ninety"};
    if(value>=1000)
    {
        convert(value/1000,s);
        string x=" Thousand";
        ll i=0;
        while(i<ll(x.size())){
        	s.pb(x[i]);
        	i++;
		}
        if(value % 1000)
        {
            if(value % 1000 < 100)
            {
                 string x=" And";
                 ll i=0;
                 while(i<ll(x.size())){
        	         s.pb(x[i]);
        	         i++;
		         }
            }
             string x=" ";
             ll i=0;
             while(i<ll(x.size())){
        	s.pb(x[i]);
        	i++;
		    }
            
            convert(value % 1000,s);
        }
    }
    else if(value >= 100)
    {
        convert(value / 100,s);
         string x=" Hundred";
        ll i=0;
        while(i<ll(x.size())){
        	s.pb(x[i]);
        	i++;
		}
        if(value % 100)
        {
             string x=" And ";
             ll i=0;
             while(i<ll(x.size())){
        	s.pb(x[i]);
        	i++;
		   }
            convert (value % 100,s);
        }
    }
    else if(value >= 20)
    {
        string x=tens[value/10];
        ll i=0;
        while(i<ll(x.size())){
        	s.pb(x[i]);
        	i++;
		}
        if(value % 10)
        {
             string x=" ";
             ll i=0;
             while(i<ll(x.size())){
        	s.pb(x[i]);
        	i++;
		    }
            convert(value % 10,s);
        }
    }
    else
    {
        string x=ones[value];
        ll i=0;
        while(i<ll(x.size())){
        	s.pb(x[i]);
        	i++;
		}
    }   
}
int main()
{
         flash;
         ll a,b;
         cin>>a>>b;
         ll ans;
         map<ll,string > mpp1;
         map<string ,ll> mpp2;
         ll arr[2];
         string srr[2];
         
         while(1){
         	
         	if(a> 99999 || b>  99999){
         		cout<<"Out of bounds";
         		break;
			 }
         	arr[0]=a;
            arr[1]=b;
            sort(arr,arr+2);
            string s1="";
            string s2="";
            //cout<<"arr[0] is "<<arr[0]<<endl;
            //cout<<"arr[1] is"<<arr[1]<<endl;
            convert(arr[0],s1);
            convert(arr[1],s2);
            mpp2[s1]=arr[0];
            mpp2[s2]=arr[1];
            
            srr[0]=s1;
            srr[1]=s2;
            sort(srr,srr+2);
             //cout<<"srr[0] is "<<srr[0]<<endl;
             //cout<<"srr[1] is"<<srr[1]<<endl;
            if(arr[0]==arr[1]){
            	cout<<arr[0];
            	break;
			}
            else if(mpp2[srr[0]]==arr[0]){
            	a=a+a;
            	b=b+b;
			}
			else if(mpp2[srr[0]]!=arr[0]){
				int ans=a+b;
				if(ans>99999){
					cout<<"Out of bounds";
				}
				else
            	cout<<a+b;
            	
            	break;
			}
		 }       
         
}
