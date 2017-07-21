# Infor_XA_DotNetHelper

The Infor_XA_DotNetHelper is intended to parse the XML response of Infor_XA and provide the simplified version of XML. It also provides response data in various .Net datatypes. It helps the .Net developers to directly use the response which comes from the Infor_XA system without painful external transformations.

Generally, the response received from Infor_XA contains some metadata (i.e.,) MetaData, descriptors, keys, domainentity, property, property paths, etc., The below are the request and response message of Infor_XA system which is being executed through System-Link.
The resultant XML is the parsed and converted response which can be utilized with other .Net data objects (datatable, dataset, list, JSON).

## XA Request :
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE System-Link SYSTEM "SystemLinkRequest.dtd"[]>
<System-Link>
	<Login userId="*****" password="*****" maxIdle="100" properties="**.**.domain.EnvironmentId=00, **.**.cas.domain.SystemName=system_name, **.**.**.user.LanguageId=en" />
	<Request sessionHandle="*CURRENT" workHandle="*new" broker="EJB" maxIdle="100">
		<QueryList name="file" domainClass="com.mapics.csm.Item" includeMetaData="true" maxReturned="1">
			<Pql>
				<![CDATA[SELECT ItemName,ItemNumber,price,quantity,weight ORDER BY Item]]>
			</Pql>
		</QueryList>
	</Request>
	<Logout sessionHandle="*CURRENT" />
</System-Link>
```

## XA Response for the above request message
```
<?xml version="1.0" encoding="UTF-8"?>
<System-Link version="1.0" hostVersion="1.0">
	<LoginResponse actionSucceeded="true">
		<SessionHandle value="-655eef2b:15bbecad567:-7a61"/>
	</LoginResponse>
	<Response sessionHandle="-655eef2b:15bbecad567:-7a61" workHandle="-655eef2b:15bbecad567:-7a60" systemTimestamp="2017-05-02 10:47:20.068" systemTimeZoneOffset="-5:00" hasErrors="false" hasWarnings="false">
		<QueryListResponse name="file" requestedDomainClass="com.mapics.csm.Item" actionSucceeded="true" moreResults="false">
			<MetaData>
				<Descriptor type="heading" path="ItemName">
					<![CDATA[ItemName]]>
				</Descriptor>
				<Descriptor type="heading" path="ItemNumber">
					<![CDATA[ItemNumber]]>
				</Descriptor>
				<Descriptor type="heading" path="price">
					<![CDATA[Price]]>
				</Descriptor>
				<Descriptor type="heading" path="quantity">
					<![CDATA[Quantity]]>
				</Descriptor>
				<Descriptor type="heading" path="weight">
					<![CDATA[Weight]]>
				</Descriptor>
			</MetaData>
			<DomainEntity domainClass="com.mapics.csm.Item">
				<Key>
					<Property path="ItemNumber">
						<Value>NBALLD</Value>
					</Property>
					<Property path="ItemName">
						<Value>
							<![CDATA[Bottle 2ml]]>
						</Value>
					</Property>
				</Key>
				<Property path="ItemNumber">
					<Value>NBALLD</Value>
				</Property>
				<Property path="ItemName">
					<Value>
						<![CDATA[Bottle 2ml]]>
					</Value>
				</Property>
				<Property path="price">
					<Value>
						<![CDATA[30.000]]>
					</Value>
				</Property>
				<Property path="quantity">
					<Value>
						<![CDATA[1]]>
					</Value>
				</Property>
				<Property path="weight">
					<Value>
						<![CDATA[56.000]]>
					</Value>
				</Property>
			</DomainEntity>
		</QueryListResponse>
	</Response>
	<LogoutResponse actionSucceeded="true"/>
</System-Link>
```

## Resultant XML

```
<?xml version="1.0" encoding="UTF-8"?>
<root>
	<ItemName>Bottle 2ml</ItemName>
	<ItemNumber>NBALLD</ItemNumber>
	<Price>30.000</Price>
	<Quantity>1</Quantity>
	<Weight>56.000</Weight>
</root>
```

The above simplified response is made using the Infor_XA_DotNetHelper library. It also supports different formats based on the methods and parameters. The code also contains inline documentation.
