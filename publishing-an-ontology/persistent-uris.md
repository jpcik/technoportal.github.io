# Adding persistent URIs to your ontology

PErsistent URIs is one of the key enablers of ontology reusability, and accessibility, which are actually fundamental to comply with the [FAIR principles](https://www.go-fair.org/fair-principles/) of data reuse. 

We can first motivate the importance of using these URIs and then how to actually implement them in practice.

## Limitations of non-dereferenceable URIs

When creating a new ontology, it is often the case that concepts are defined using a base URI that does not necessarily can be dereferenced.

For example if you create an ontology about *Wind turbines*, perhaps in a first version the base URI for all concepts will be something like:

```
@prefix wind: <http://example.org/turbine-onto#>
```

**Note: ** We are using Trutle format for all examples.

Of course this URI cannot be dereferenced, it is simply a placeholder that is used during the development process.
Them if we have a concept `wind:Turbine`, its full URI will be `http://example.org/turbine-onto#Turbine`

This URI is not an existing web location, so if someone uses it, they cannot get additional information about it, they cannot get documentation nor links towards other relevant data about it.

## Limitations of non-persistent URIs

To solve this problem, it is important that the ontology is made available on the Web, so that others can use it and so that the concepts that it defines can be referenced and reused.

Moreover, even if we publish the ontology in a public URI, it is essential that these URIs persist in time, so to avoid that links are broken in the future.

For example, imagine that you publish your ontology in your company website at:

```
   https://my-conpany.com/myontologies/wind-turbines-ontology.owl
```

Moreover, knwoing that this is the base URIs, if there is a `Turbine` concept inside the ontology, it may be referenced as:

```
https://my-conpany.com/myontologies/wind-turbines-ontology.owl#Turbine
```

Now people can access the ontology online and potentially get more information and documentation about it. 

However, what happens if you decide to change the organization of the folders, for example liek this:

```
   https://my-conpany.com/knowledge/wind/wind-turbines-ontology.owl
```

In that case if anyone was referencing your ontology, the links will be broken. Even more, if your company is merged with another one, maybe even your domain may change:

```
   https://big-firm.com/knowledge/wind/wind-turbines-ontology.owl
```

And again links are broken.

## Permanent URI providers

To solve these problems, there exist services that allow creating persistent URIs. 
These URIs are designed to be maintained immutable over time, while they may redirect requests to real URLs if needed. Example of these providers are [purl.org](https://purl.archive.org/), and [w3id.org](w3id.org).

For example