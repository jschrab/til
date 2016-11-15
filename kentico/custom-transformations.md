# Custom Transformations

Categories are separate (true?) from Documents. You can look up which documents belong to which categories. This gets messy in a


```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;

using System.Data;

using CMS.DocumentEngine;
using CMS.Taxonomy;
using CMS.Helpers;

namespace CMS.Controls
{
    /// <summary>
    /// Extends the CMSTransformation partial class.
    /// </summary>
    public partial class CMSTransformation
    {
        public string GetDocumentCategories(int documentId, string documentListAliasPath)
        {
            if (documentId < 1)
            {
                throw new Exception("Invalid document ID");
            }

            // Uses the current document's alias path if one is not specified
            if (documentListAliasPath == null)
            {
                documentListAliasPath = DocumentContext.CurrentAliasPath;
            }

            // Initializes the HTML code result
            string result = "";

            // Gets the categories of the specified document
            DataSet ds = CategoryInfoProvider.GetDocumentCategories(documentId, null, null, 0, "CMS_Category.CategoryID, CategoryDisplayName");

            if (!DataHelper.DataSourceIsEmpty(ds))
            {
                foreach (DataRow row in ds.Tables[0].Rows)
                {
                    // Constructs links for the assigned categories
                    // The links lead to a page containing a list of documents that belong to the same category, with the category ID in the query string
                    int categoryId = ValidationHelper.GetInteger(row["CategoryID"], 0);
                    string categoryName = ValidationHelper.GetString(row["CategoryDisplayName"], null);

                    result += "<a href=\"" + URLHelper.ResolveUrl(DocumentURLProvider.GetUrl(documentListAliasPath));
                    result += "?category=" + categoryId;
                    result += "\">" + categoryName + "</a>&nbsp;";
                }
            }

            return result;
        }
    }
}
```


Source: https://docs.kentico.com/display/K8/Example+-+Displaying+categories+in+document+lists
