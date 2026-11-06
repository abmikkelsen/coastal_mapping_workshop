# coastal\_mapping\_workshop

A hands-on workshop from the Hawaii Data Science Institute on mapping shorelines from satellite imagery. We start with why shorelines matter and how they are monitored, then work through a Jupyter notebook: load Sentinel-2 images, extract a shoreline with a water index (NDWI) and a threshold, measure its position along a transect, and build a time series. We finish by looking at noise, filtering, seasonality and tide correction, and ask what satellite shorelines can and cannot tell us.

## Option A: Use Google Colab 
[link to colab notebook](https://colab.research.google.com/drive/13Lv73ncu1_Rm3nR_BphhaLkZ3GCycKi7?usp=sharing)

(if everything breaks, [here](https://colab.research.google.com/drive/1-MStSA6N9WNlKPBthrIHNvOjee3whGKE#scrollTo=4c3e125b) is a notebook with outputs already generated)

## Option B: Setup locally

### 0\. Clone the repo

```bash
git clone https://github.com/abmikkelsen/coastal_mapping_workshop.git
cd coastal_mapping_workshop
```

### 1\. Create the environment

Open a terminal (Anaconda Prompt on Windows), `cd` into the `coastal\_mapping\_workshop` folder, then:

```bash
conda env create -f environment.yml
conda activate coast
```

### 2\. Install geedownload (only needed to download imagery)

```bash
pip install --no-cache-dir git+https://github.com/Coastal-Research-Collaborative/geedownload.git
```

If the install fails, install GDAL and git with conda (git must be available so pip can fetch from GitHub), then run the pip command again:

```bash
conda install -c conda-forge gdal
conda install -c conda-forge git
pip install --no-cache-dir git+https://github.com/Coastal-Research-Collaborative/geedownload.git
```

### 3\. Start the notebook
in VS code or jupyter lab
```bash
jupyter lab
```

then open the workshop notebook.

## Getting Google Earth Engine access

You only need this to download new imagery. The workshop images are provided, so you can skip it for the hands-on part.

1. Sign in with a Google account.
2. Register for Earth Engine as **noncommercial** (free for research, education and personal use): https://earthengine.google.com/noncommercial. You will be asked to create or choose a Google Cloud project, and to complete a short verification questionnaire in the Cloud console.
3. Note your **project ID**. Earth Engine requires a Cloud project with the Earth Engine API enabled. You can create one at https://console.cloud.google.com/projectcreate, and enable the API at https://console.cloud.google.com/apis/library/earthengine.googleapis.com. If you already have a project, you can register it at `https://code.earthengine.google.com/register?project=YOUR\_PROJECT\_ID`.
4. In Python, log in once and start Earth Engine with your project:

```python
   import ee
   ee.Authenticate()                      # opens a browser window to log in
   ee.Initialize(project="YOUR\_PROJECT\_ID")
   ```
More: [Earth Engine access guide](https://developers.google.com/earth-engine/guides/access) and [authentication guide](https://developers.google.com/earth-engine/guides/auth). CoastSat (see link below) also has a simple how-to tutorial

## Learn more

* [geedownload](https://github.com/Coastal-Research-Collaborative/geedownload): download Landsat and Sentinel-2 imagery from Earth Engine for a polygon and date range
* [CoastSat](https://github.com/kvos/CoastSat): the established open-source toolkit for satellite shoreline mapping at scale (Vos et al., 2019, https://doi.org/10.1016/j.envsoft.2019.104528)
* [eo-tides](https://github.com/GeoscienceAustralia/eo-tides): tide modelling for satellite imagery
* Estimating beach slope from satellite shorelines: https://doi.org/10.1029/2020GL088365
* Seasonal shoreline behaviour (erosion fast, recovery slow): https://doi.org/10.1029/2024JF007836

