# # Codefresh Monorepo example

This is a monorepo with multiple trigger and single pipeline example to demonstrate codefresh muti trigger, annotation and cli as an option to gate control the cd part.


# Monorepo Details

Repo contains multiple microservice namely users,  products,items etc under the folder  **packages**

## Codefresh Piepline

The pipeline that build indidual services based upon individual service glob expression based trigger is in  **./cf/codfresh.yaml** 

## Glob expression for the individual services build trigger.

Though all the service can be manged using a single trigger, for the purpose demonstrating multi trigger following 2 trigger are enabled to build  **products** and  **users** as separate trigger event.
 1. Glob expression for  **products** ** - ***packages/products/*****
 2. Glob expression for  **users** ** - ***packages/users/*****

## How to use this pipeline 

To use this pipeline
  1. Clone this repo
  2. Create a new pipeline and replace the content with **./cf/codfresh.yaml** or use the location of this or cloned  repo, **./cf/codfresh.yaml** as the pipeline repo location.
  3. add the 2 triggers mentioned in the  **Glob expression ** section above.
  4. Add a pipeline variable by name **RELEASE_NAME**

## How to use this pipeline 

To test this pipeline, after creating a piepline as menitoned in the previouse section **How to use this pipeline **.
1. Do a non breaking change to one of the file in ***packages/products/*** folder
2. commit the change with the commit message containing the kye word required for the **products**. The key word in the comment is ***products_build***

> E.g a comment like "testing monorepo for prodcuts, products_build"
>
3. Watch the new build for prodcuts service. This should not run the deploy step yet,as all the required services are not ready yet.
4. Do a non breaking change to one of the file in ***packages/users/*** folder
5. . commit the change with the commit message containing the kye word required for the **users**. The key word in the comment is ***users_build***
6. Watch the new build for users service. This should now run the deploy step yet,as all the required services are not ready by now.

