# ================================
# Crawl4AI + Playwright Base Image
# ================================

FROM python:3.11-slim

LABEL maintainer="crawl4ai-base"
LABEL description="Reusable base image with crawl4ai + Playwright + browsers"

ENV DEBIAN_FRONTEND=noninteractive
ENV PYTHONUNBUFFERED=1
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# ----------------
# System packages
# ----------------
RUN apt-get update && apt-get install -y \
    wget \
    curl \
    unzip \
    git \
    ca-certificates \
    fonts-liberation \
    libasound2 \
    libatk1.0-0 \
    libatk-bridge2.0-0 \
    libcups2 \
    libdrm2 \
    libxkbcommon0 \
    libxcomposite1 \
    libxdamage1 \
    libxfixes3 \
    libxrandr2 \
    libgbm1 \
    libgtk-3-0 \
    libnss3 \
    libxshmfence1 \
    libx11-xcb1 \
    libxcb1 \
    libxext6 \
    libxrender1 \
    libxinerama1 \
    libxcursor1 \
    libxi6 \
    libpangocairo-1.0-0 \
    libpango-1.0-0 \
    libjpeg62-turbo \
    libpng16-16 \
    libwebp7 \
    libegl1 \
    libopengl0 \
    xvfb \
    && rm -rf /var/lib/apt/lists/*

# ----------------
# Python deps
# ----------------
RUN pip install --upgrade pip setuptools wheel

RUN pip install \
    crawl4ai \
    playwright \
    requests \
    beautifulsoup4 \
    lxml \
    aiohttp \
    fake-useragent \
    cloudscraper \
    python-dotenv

# ----------------
# Playwright browsers
# ----------------
RUN playwright install --with-deps

# Default working dir
WORKDIR /app

# Base image should NOT run anything
CMD ["python"]
