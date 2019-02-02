---
layout: home
title: "Code"
---


# Test Code For HW1

```matlab
function [Klocal]=Truss3D(Coor1,Coor2,Coor3,A,E,type,n)
 
%Defining the coordinates for the nodes of the triangular elements
X1=Coor1(1);
Y1=Coor1(2);
X2=Coor2(1);
Y2=Coor2(2);
X3=Coor3(1);
Y3=Coor3(2);
%equivalent coordinate matrix
XE=[X1,X2,X3];
YE=[Y1,Y2,Y3];
 
Area=polyarea(XE,YE);
 
B=(1/(2*Area))*[(Y2-Y3),0,(Y3-Y1),0,(Y1-Y2),0;0,(X3-X2),0,(X1-X3),0,(X2-X1);(X3-X2),(Y2-Y3),(X1-X3),(Y3-Y1),(X2-X1),(Y1-Y2)];
 
if type ==2 %plain stress
    
    D=E/(1-nu^2)*[1,nu,0;nu,1,0;0,0,(1-nu)/2];
end
 
if type ==3 %plain strain
    D=E/((1+nu)*(1-2*nu))*[(1-nu),nu,0;nu,(1-nu),0;0,0,(1-2*nu)/2];
end
 
 
Klocal=(A*Area)*(B'*D*B);
 
    return
    
end
```






