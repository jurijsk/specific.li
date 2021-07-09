# Notes on Google Analitics (Universal Analytics) Mesurement Protocol and Enhanced Ecommerce with Custom Dimensions

When sending custom events for Enhanced Ecommerce with custom dimension values, you can send them eather as `cd` params,
product parameters 'pr<productIndex>cd<dimensionIndex>' (`pr..`), or as Impression List Product Impressions parameters il<listIndex>pi<productIndex>cd<dimensionIndex>.

You can send data with click `product action` (`pa=click`) as `cd..` params but dimension should be hit-scoped.

You can send data as `pr..` parameter if dimension is product-scoped. 
  
You can send differend values for the same `productId` as `pr..` parameters even though dimension is product-scoped.
  
You can not send product-scoped params as `cd..` params.
  
Same goes for `il` params
