# magento2-prismicio-sample-data
Magento 2 Prismic Sample Data

## Exampple of real world example

The prismic json for a landing page custom type. The type has a number of multifunctional slices, and some elements in the main zone.

```json
{
  "Main" : {
    "uid" : {
      "type" : "UID",
      "config" : {
        "label" : "UID"
      }
    },
    "title" : {
      "type" : "StructuredText",
      "config" : {
        "single" : "heading1,heading2,heading3,heading4,heading5,heading6",
        "label" : "Title"
      }
    },
    "description" : {
      "type" : "StructuredText",
      "config" : {
        "multi" : "paragraph,preformatted,heading1,strong,em,hyperlink,image,embed,list-item,o-list-item",
        "allowTargetBlank" : true,
        "label" : "Description"
      }
    },
    "body" : {
      "type" : "Slices",
      "fieldset" : "Slice zone",
      "config" : {
        "labels" : null,
        "choices" : {
          "text_block" : {
            "type" : "Slice",
            "fieldset" : "Text Block",
            "description" : "Description",
            "icon" : "adb",
            "display" : "list",
            "non-repeat" : {
              "content" : {
                "type" : "StructuredText",
                "config" : {
                  "multi" : "paragraph,preformatted,heading1,heading2,heading3,heading4,heading5,heading6,strong,em,hyperlink,embed,list-item,o-list-item",
                  "label" : "Text",
                  "placeholder" : "Content"
                }
              },
              "center" : {
                "type" : "Boolean",
                "config" : {
                  "default_value" : false,
                  "label" : "Center Text"
                }
              },
              "link_title" : {
                "type" : "StructuredText",
                "config" : {
                  "single" : "strong,em",
                  "label" : "Link Title"
                }
              },
              "link" : {
                "type" : "Link",
                "config" : {
                  "label" : "Link",
                  "select" : null
                }
              }
            },
            "repeat" : { }
          },
          "full_width_image" : {
            "type" : "Slice",
            "fieldset" : "Full Width Image",
            "description" : "Banner 100% width",
            "icon" : "image",
            "display" : "list",
            "non-repeat" : {
              "full_width_image" : {
                "type" : "Image",
                "config" : {
                  "constraint" : { },
                  "thumbnails" : [ {
                    "name" : "mobile",
                    "width" : 640,
                    "height" : 320
                  } ],
                  "label" : "Full width Image"
                }
              },
              "full_width_image_url" : {
                "type" : "Link",
                "config" : {
                  "label" : "URL",
                  "placeholder" : "https://{{relative}}",
                  "select" : null
                }
              }
            },
            "repeat" : { }
          },
          "list_items_with_image" : {
            "type" : "Slice",
            "fieldset" : "List Items With Image",
            "description" : "Items with image",
            "icon" : "art_track",
            "display" : "list",
            "non-repeat" : {
              "header" : {
                "type" : "StructuredText",
                "config" : {
                  "single" : "paragraph,strong,em",
                  "label" : "Header"
                }
              },
              "image" : {
                "type" : "Image",
                "config" : {
                  "constraint" : {
                    "width" : 262,
                    "height" : 262
                  },
                  "thumbnails" : [ ],
                  "label" : "Image"
                }
              }
            },
            "repeat" : {
              "icon" : {
                "type" : "StructuredText",
                "config" : {
                  "single" : "rtl",
                  "label" : "Icon"
                }
              },
              "label" : {
                "type" : "StructuredText",
                "config" : {
                  "single" : "paragraph,strong,em,hyperlink",
                  "label" : "Label"
                }
              }
            }
          },
          "large_image_with_text" : {
            "type" : "Slice",
            "fieldset" : "Large Image with text",
            "description" : "Image with text",
            "icon" : "aspect_ratio",
            "display" : "list",
            "non-repeat" : {
              "image" : {
                "type" : "Image",
                "config" : {
                  "constraint" : {
                    "width" : 825,
                    "height" : 652
                  },
                  "thumbnails" : [ {
                    "name" : "mobile",
                    "width" : 640,
                    "height" : 320
                  } ],
                  "label" : "Image"
                }
              },
              "image_url" : {
                "type" : "Link",
                "config" : {
                  "label" : "Image Url",
                  "select" : null
                }
              },
              "content" : {
                "type" : "StructuredText",
                "config" : {
                  "single" : "paragraph,heading2,heading3,heading4,heading5,heading6,strong,em,hyperlink",
                  "label" : "Content"
                }
              }
            },
            "repeat" : { }
          },
        }
      }
    }
  },
  "SEO" : {
    "meta_title" : {
      "type" : "Text",
      "config" : {
        "label" : "Meta title"
      }
    },
    "meta_description" : {
      "type" : "Text",
      "config" : {
        "label" : "Meta description"
      }
    },
    "body2" : {
      "type" : "Slices",
      "fieldset" : "Slice zone",
      "config" : {
        "labels" : { },
        "choices" : { }
      }
    }
  }
}
```

This example prismic custom type is configured using the `view/frontend/layout/prismicio_by_type_landing_page.xml` file. Herein a number of slice types are configured that are a part of the prismic json here above. The slices need to be added to the xml using an update element, `<update handle="prismicio_slices_text_block"/>`. They then also need to be placed inside the `prismicio_content` element using the move element; `<move element="text_block" destination="prismicio_landingpage.slices" as="prismicio_landingpage.slices.text_block" />`.

The different slices of this custom type are configured using the `view/frontend/layout/prismicio_slices_slice_type.xml` files.

## XML file naming `priscimio_by_type_...`, `prismicio_slices_...`

Using an xml file named `prismicio_by_type_custome_type.xml`, where 'custom_type' is replaced by the type in question. This will target that prismic custom type. 

Similarly, files named `prismicio_slices_slice_name.xml`, where 'slice_name' is the name of the slice. Will target the slice with that name.
