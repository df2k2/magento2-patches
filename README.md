# Magento2 Patches

-------

## Purpose

Magento2 patches automatically applied based on current magento2 version


----

## Installation

Under Magento2 root composer.json (`<magento_root>/composer.json`), 

* Add dependency to **require** node
* Add repository information
* Add "Extra" options

```json

...
  "require": {
      ...
      "df2k2/magento2-patches":"dev-master",
      ...
  },
  ...
  "repositories": [
      {
          "type": "composer",
          "url": "https://repo.magento.com/"
      },
      {
          "type": "github",
          "url": "https://github.com/df2k2/magento2-patches"
      }
   ],
   "extra": {
        "magento-force": "override",
        "patcher": {
            "appliers": {
                "GIT": {
                    "ping": "[[bin]] rev-parse --is-inside-work-tree"
                }
            }
        },
        "patcher-windows": {
            "appliers": {
                "PATCH": {
                    "bin": "where patch /F"
                },
                "GIT": {
                    "ping": "[[bin]] rev-parse --is-inside-work-tree",
                    "bin": "where git /F"
                }
            }
        }
    }

```
