# Boutiqaat Men's Apparel Scraper Pipeline - Group 2

Automated web scraping pipeline for Boutiqaat men's apparel products (Group 2) with S3 storage and Excel report generation.

## Features

✅ **Automated Web Scraping**
- Scrapes men's apparel subcategories from boutiqaat.com
- Extracts detailed product information (name, price, brand, description, ratings, etc.)
- Handles infinite scroll pagination automatically

✅ **Image Management**
- Downloads product images from the website
- Uploads to AWS S3 with organized folder structure
- Generates S3 paths for reference in Excel files

✅ **Excel Report Generation**
- Creates one Excel file per category
- Separate worksheet for each subcategory
- Includes summary statistics
- Professional formatting with colors and borders
- S3 image path column for easy reference

✅ **S3 Storage with Date Partitioning**
- Organized folder structure: `bucket/boutiqaat-data/year=YYYY/month=MM/day=DD/men/apparel/`
- Separate folders for images and Excel files
- Easy to query and organize data by date

## Scraped Categories - Group 2

This pipeline scrapes the following men's apparel subcategories:
1. Kidswear
2. T-Shirts & Tanks
3. Hoodies & Sweatshirts
4. Cardigans & Sweaters
5. Joggers & Sweatpants
6. Shorts

## Running the Scraper

From the project root directory:
```bash
python -m men_apparel_sub2.main
```

## Output

### Excel Files
- Location: S3 → `boutiqaat-data/year=YYYY/month=MM/day=DD/men/apparel/excel-files/`
- Format: `{category_name}_{timestamp}.xlsx`

### Images
- Location: S3 → `boutiqaat-data/year=YYYY/month=MM/day=DD/men/apparel/images/{category}/`
- Format: `{sku}_image.jpg`

## Async Processing

The pipeline processes up to 3 subcategories concurrently using asyncio with a semaphore to prevent overwhelming the server.
