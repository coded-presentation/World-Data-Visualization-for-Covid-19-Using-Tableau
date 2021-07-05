# Global Infection Vs Vaccination Visualization in Tableau (Part - 2)
<h3>This Portfolio is based upon the OurWorldInData Project done by MIT and Standford University.
</h3>
<p>In this Portfolio i have mentioned several Queries that are used to find Views for attaching it on to tableau for visualization.</p>
 

<!---->        

<!--<a href="" ><img src=""> </a>-->
 
</a>

<h2> About Me</h2>
<a href="https://www.linkedin.com/in/karan-shah-020b4baa"><img src="https://media-exp3.licdn.com/dms/image/D5635AQGENREQtSOVvA/profile-framedphoto-shrink_400_400/0/1624892028859?e=1625497200&amp;v=beta&amp;t=nHSeFvfJ5joOESVOVAkxRgNxPjWHCPtUIR6yaMmysBE" height="100" alt="KARAN SHAH, #OPEN_TO_WORK" id="ember53" class="profile-photo-edit__preview ember-view">
</a>
<h3>
            KARAN SHAH
</h3>
<h4>
            Computer Engineer / Data Analyst / Pursuing Google Data Analytics Professional Certificate
</h4>
<h2> Portfolio Project (Part - 2)</h2>


<h4>Covid 19 Data Visualization</h4>


>{Skills used: Joins, CTE's, Temp Tables, Windows Functions, Aggregate Functions, Creating Views, Converting Data Types}

>Countries with Highest Infection Rate compared to Population
```
Select Location, Population, MAX(total_cases) as HighestInfectionCount,  Max((total_cases/population))*100 as PercentPopulationInfected
From PortfolioProject..CovidDeaths
--Where location like '%India%'
Group by Location, Population
order by PercentPopulationInfected desc
```


 **Output  for sheet-1**
<a This image is of finding the total population affected by Covid-19 Infection href=""><img src="https://bn1305files.storage.live.com/y4mwr5YbLVW5qEqGcSZ3lOpUbgvqmXj5qvdztvI5qgueLNHdnUQ3XHnaY8fP7BmWLQuHZSrPUIozSrDj0zdu0SnsQap1I2yZY5g4-_iwsvkhJybeW04fJLyi2wPbKo48MVZC3dhRgBy3sXP4KVEkP2OXZLbY024qYOCrUBo8Rb9SQy3Md9cVeNabuzEh5hVfPH8?width=1864&height=1080&cropmode=none"> </a>

>Countries with Highest Death Count per Population

```
Select SUM(new_cases) as total_cases, SUM(cast(new_deaths as int)) as total_deaths, SUM(cast(new_deaths as int))/SUM(New_Cases)*100 as DeathPercentage
From PortfolioProject..CovidDeaths
--Where location like '%states%'
where continent is not null 
--Group By date
order by 1,2

```
 **Output  for Sheet-2**
<a =""> <img src="https://bn1305files.storage.live.com/y4m_OnoC7Ahsd7YaW3hj2b01xKZtFRZbvcs1RAI9ufqjGjx-xBeGo3kGgss9ufradp3T1-1HQKAKJMd2X8BBjzFDUifGjL4gLp_T94bo22nRyxNDaDwNhPOs8I4OYYJ8mOnm_XxpPYrFWHhh6QDjmezbUjcvEo86epInCT6_PGyb29o_PcSCa2_zw_qagDwoKXY?width=1925&height=1079&cropmode=none"></a>     

>BREAKING THINGS DOWN BY CONTINENT
>Showing Total Deaths per continent
```
-- We take these out as they are not inluded in the above queries and want to stay consistent
-- European Union is part of Europe

Select location, SUM(cast(new_deaths as int)) as TotalDeathCount
From PortfolioProject..CovidDeaths
--Where location like '%states%'
Where continent is null 
and location not in ('World', 'European Union', 'International')
Group by location
order by TotalDeathCount desc

```
 **Output  for sheet-3**
<a href="" ><img src="https://bn1305files.storage.live.com/y4mu1tGfb3OtKcqLc5b6lVSDPFsARFZJhpIEHv3wds_XGBX3mLE54lp-txIBP6i6OEuJIUcv_mHfaHWrxoA-cmcpiLlnPIZYKoNoIcGOGb9KuFFQ8VbFx57R-G-9vvF_C99NTvH5EccPHlWNogd8gcw3y6Zwatzt19x7gRWhordi3rT7vIHXp6-M9X_jDe1gbtt?width=1929&height=1080&cropmode=none"> </a>
>GLOBAL NUMBERS
>This view i ceated to show percent population infection per country by Geo-location
```
Select Location, Population, MAX(total_cases) as HighestInfectionCount,  Max((total_cases/population))*100 as PercentPopulationInfected
From PortfolioProject..CovidDeaths
--Where location like '%states%'
Group by Location, Population
order by PercentPopulationInfected desc


```
 **Output  for sheet-4**
<a href="" ><img src="https://bn1305files.storage.live.com/y4mwBGVLPa88LMfEK0bw2iXx9KIHYDKucKiDZ6sgrQ_qrzvt1Lm8C-RwNzO-9hx_yaM2Y7McGwn3On_vgv2LhHJ6Xqn6BaeUYHhMa5pNmNFrtn9gTRoQM8ecbbWPSUxIoS9HfN72kPt0YVc0HLITZK3ri4ZkwjCmt19p3KbvQ0c76ZdBKk7P1ouRePDby_7mtTY?width=1928&height=1080&cropmode=none"> </a>
>Total Population vs Vaccinations
>Shows Percentage of Population got the infection and The projectile graph for different countries.
```

Select Location, Population,date, MAX(total_cases) as HighestInfectionCount,  Max((total_cases/population))*100 as PercentPopulationInfected
From PortfolioProject..CovidDeaths
--Where location like '%states%'
Group by Location, Population, date
order by PercentPopulationInfected desc


```
 **Output  for Table 5**
<a href="" ><img src="https://bn1305files.storage.live.com/y4me1k3MMQYG4MPpOfKdFiL8CJh8_ki-heOxErVu_GSw3rOle4ps5fs8Ra4KangoDCMQ3pL-BVMRBJTRPJ_Zkb-GYjUranKBZd1phByMrt8Lkg6FWeyd2eXoVR8icJKpLOW52pB7HfVW86_ACJQsGGborCSv9f7ZjpTd-EisKYt6zNmK6wGQ56Eq_1ClkCvuyy6?width=1925&height=1079&cropmode=none"> </a>
>Using CTE to perform Calculation on Partition By in previous query

<!--\-->


#Go To Tablue Deskop and review my work 
					   
<a href="https://prod-apnortheast-a.online.tableau.com/t/tableauprofessinals/views/CovidDashboardWorkbook/Dashboard1/kshah.pro@gmail.com/77a7c19a-a213-449d-a1b0-ec3b331970fc?:display_count=n&:showVizHome=n&:origin=viz_share_link"><img src="https://bn1305files.storage.live.com/y4mEoYRgATab49RvcnKBBXbH4JJhTS2mcbZo6BIw5ISHJNkuVbgt5dXCbnd4lLcFru5miS4E2Z-2zmc_CBNuccwyEGcPdfocYir781NIKhSBCrX0F7jWrSZnK-2jhnvSM3TbQk4qlEawKNrFY5_p3e2U5k0C4rk_8crFJA1Lo6cZjeN9CLEbPi7rihcsdH0EENr?width=1936&height=1079&cropmode=none"></a>
