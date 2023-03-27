# Matplotlib-Challenge

The following lines of code were aided by Github user: "benanza"
The location is under header: "Quartiles, Outliers and Boxplots"

    for treatment in Treatments:
    
        regiment = combined_df.loc[combined_df['Drug Regimen'] == treatment]

        timepoint_df = regiment.loc[regiment['Timepoint'] == regiment['Last Timepoint']]

        tumor_volume = timepoint_df['Tumor Volume (mm3)']
        tumor_vol_data.append(tumor_volume)   
    
        quartiles = tumor_volume.quantile([.25,.5,.75])
        lowerq = quartiles[0.25]
        upperq = quartiles[0.75]
        iqr = upperq-lowerq
        iqr = upperq-lowerq
        print(f'The IQR for {treatment}: {iqr}')

        lowerbound = lowerq - 1.5*iqr
        upperbound = upperq + 1.5*iqr
        print(f'The Upper Bound for {treatment}: {upperbound}')
        print(f'The Lower Bound for {treatment}: {lowerbound}')
    
The following lines of code were aided by ChatGPT:
The location is under header: "Line and Scatter Plots"
    
    capomulin_df = cleaned_df.loc[cleaned_df['Drug Regimen'] == 'Capomulin']
    tumor_vol_avg = pd.DataFrame(capomulin_df.groupby('Mouse ID')['Tumor Volume (mm3)'].mean().sort_values()).reset_index().rename(columns={'Tumor Volume (mm3)': 'avg_tumor_vol'})

The following lines of code were aided by ChatGPT:
The location is under header: "Correlation and Regression"

    correlation = st.pearsonr(final_avg_vol_df['Weight (g)'], final_avg_vol_df['avg_tumor_vol'])
    regress_values = final_avg_vol_df['Weight (g)'] * slope + intercept
    line_best_fit = "y = " + str(round(slope,2)) + "x + " + str(round(intercept,2))
