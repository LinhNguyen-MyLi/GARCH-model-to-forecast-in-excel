# GARCH-model-to-forecast-in-excel-
I apply fundamental knowledge related to the GARCH model to make forecast the volatility of return of 10 big firms in the IT industry
Build up GARCH (1,1) model using Maximum Likelihood to predict the volatility of return on stock prices of 10 firms. You could read the following steps to get more insight into forecasting with the GARCH model:

1. In the model, we have 03 parameters: alpha (α), beta (β), and gamma (γ). The sum of those parameters must be equal to 1. We will use those 03 parameters to compute the long-run average variance rate as the formula below: <br/> 
$~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~$  ![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/553e4dff-e0a5-464a-9c34-7abe6931af7f) <br/>
We set ![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/66e80769-0f73-4269-a8ad-ff1ef93d4bf0)  with VL stand for long run daily variance => the formula change into: <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/47cf1121-7cd7-4210-b7ba-a2d8fec2ee36) <br/>
With sum of 03 parameters equal to 1 => γ=1- α- β we have the formula: <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/15bf331f-4ff7-4e31-98f5-e18b7839a72f) <br/>
Before running the solver we assume the following initial values for α, β, ω as follows: <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/e3fb58d3-ab34-442a-93ad-c54c4489fff9) <br/>
Based on those initial values and the formula V, we calculate long-run daily variance, then take the square root of V_L to obtain Long run daily Std, then by multiplying the Long run daily Std with the square root of 250 (number of trading days in a year), we achieve its annual value.
The result for parameters before running the solver (the result for DELL):<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/1d161eb9-b5ab-48ac-9508-92a3aaeff3f3)

2. We use the maximum likelihood method in this case instead of regular regression cause in this case, our data (the volatility of the rate of return) tends to fluctuate over time, and in traditional regression, it is often assumed that the errors (or residuals) have constant volatility. In maximum likelihood methods, we choose parameters that maximize the probability of observing the given rate of return data, in other words, choose the parameter that maximizes the likelihood function below, this function measures the probability of obtaining the observed data:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/8d89d22d-0d8b-4e46-82cb-42bed64f4e8d) <br/>
=> To  obtain the result for the function, firstly, we need to calculate the ui and v or σ_n^2 (variance of Ut). The Ut  is the rate of return, it's calculated as the formula: ![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/964ed13f-802b-43c4-a4b7-16085e5767bd). As for the Variance of Ut, the first volatility value equal to power 2 of the first ut, the second variance value is calculated as the formula:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/a77da86a-177f-42aa-93fd-d300cd702a09) <br/>
After achieving the value of ui and Rt we can compute the likelihood function. The result will look like this (DELL):<br/>
![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/169970bf-88f1-4fff-9e92-b4afa68ed251) <br/>
(Note: for calculating the Annual Std before the GARCH model we multiply square root of 250 with the square root of daily return)<br/>

3. After the step 2 we should achieve the Sum of likelihood function. Next step, we use the Solver function for set a constrain for parameters (γ, α, β). As we have already mentioned above those parameters should be settled in the range from 0 to 1. And the sum of them must be equal to 1. The constrain input into Solver should be like this: <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/d070d5f8-343e-4ae0-8947-b5226f2120e8) <br/>
After running the Solver, we will obtain a new set of parameters that maximize the Sum of the likelihood function. The result for DELL: <br/>
![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/fa629670-32e4-4d80-9f32-6054df3f0bd3) <br/>

4. Recalculate the feature in step 2 with this new set of parameters. The result will be like below:<br/>
![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/561f4a8f-e7d8-4f78-88ba-4a366e56369b) <br/>
We also added 03 new features: GARCH Modeled Daily Std, GARCH Modeled Annual Std Dev and Long Run Annual Std. Computing the daily Std and Annual Std is the same as in I. As for Long run annual Std, we simply take Long run annual Std in the parameter table in step 3. The table result will be like this: <br/>
![image](https://github.com/LinhNguyen-MyLi/GARCH-model-to-forecast-in-excel/assets/128978862/f85204ee-5c49-466b-98a2-3dcfae996d74) <br/>

5. Forecased Standard Deviation over 300 days ahead



