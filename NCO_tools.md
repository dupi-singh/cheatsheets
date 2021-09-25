NCO Tools - Manipulate netCDF files from Command line
-----------------------------------------------------

| Operator | Full Name                  |
| -------- |:-------------------------- |
| `ncap2` | netCDF Arithmetic Processor |
| `ncatted` | netCDF ATTribute EDitor   |
| `ncbo` | netCDF Binary Operator       |
| `ncclimo` | netCDF CLIMatOlogy Generator |
| `nces` | netCDF Ensemble Statistics   |
| `ncecat` | netCDF Ensemble conCATenator |
| `ncflint` | netCDF FiLe INTerpolator  |
| `ncks` | netCDF Kitchen Sink          |
| `ncpdq` | netCDF Permute Dimensions Quickly, Pack Data Quietly |
| `ncra` | netCDF Record Averager       |
| `ncrcat` | netCDF Record conCATenator |
| `ncremap` | netCDF REMAPer          |
| `ncrename` | netCDF RENAMEer          |
| `ncwa` | netCDF Weighted Averager     |



### Example

| Usage | Command |
|--|--|
| Version |	ncks --version |
| Switches |	-O overwrite <br> -A append |
| List metadata |	ncdump -h file.nc;  ncks -M file.nc |
| Rename Variable |	ncrename -O -v var1,newvar filein.nc fileout.nc |
| Rename dimension |	ncrename -O -d x,lon filein.nc fileout.nc |
| Subset/crop nc file |	ncks -F -d time,1,10 filein.nc fileout.nc <br> -F option tells to use Fortran indexing i.e. from 1 <br> ncks -d lat,-30.0,30.0 filein.nc fileout.nc <br> Note: dots are compulsory, otherwise 30 will be treated as index |
| Only keep var1 and var2 |	ncks -O -v var1,var2 filein.nc fileout.nc |
| Remove variables var1 and var2	| ncks -O -x -v var1,var2 filein.nc fileout.nc |
| Merge two files	| ncks -A file1.nc file2.nc <br> Also called appending. The variables can be different but should have same dimensions |
| Make time dimension unlimited |	ncks -O --mk_rec_dmn time filein.nc fileout.nc |
| concatenate files |	Ncrcat f1.nc f2.nc f3.nc fout.nc |
| delete attribute “standard_name” for variable “var1”	| ncatted -a standard_name,var1,d,, filein.nc fileout.nc |
| modify existing attribute “long_name” of character type for variable var1	| ncatted -a long_name,var1,m,c,'temperature' filein.nc fileout.nc |
| create non-existing attribute “units” of character type for variable var1	| ncatted -a units,var1,c,c,'K' filein.nc fileout.nc |
| To calculate new variable called KE from existing uu and vv variables |	ncap2 -F -s "KE=0.5*(uu * uu+vv * vv)" file_in.nc file_out.nc |
	
	
	
	
	
	
	
	
	
	
	
	
	
	
