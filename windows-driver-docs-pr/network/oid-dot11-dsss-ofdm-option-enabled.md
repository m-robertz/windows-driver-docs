---
title: OID_DOT11_DSSS_OFDM_OPTION_ENABLED
author: windows-driver-content
description: OID\_DOT11\_DSSS\_OFDM\_OPTION\_ENABLED
ms.assetid: 17d1b975-093d-4d82-bbb9-3f678e8e4ac8
ms.author: windowsdriverdev
ms.date: 08/08/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
keywords: 
 -OID_DOT11_DSSS_OFDM_OPTION_ENABLED Network Drivers Starting with Windows Vista
---

# OID\_DOT11\_DSSS\_OFDM\_OPTION\_ENABLED


**Important**  The [Native 802.11 Wireless LAN](https://msdn.microsoft.com/library/windows/hardware/ff560690) interface is deprecated in Windows 10 and later. Please use the WLAN Device Driver Interface (WDI) instead. For more information about WDI, see [WLAN Universal Windows driver model](https://msdn.microsoft.com/library/windows/hardware/dn897672).

 

When queried, the OID\_DOT11\_DSSS\_OFDM\_OPTION \_ENABLED object identifier (OID) requests that the miniport driver return the value of the IEEE 802.11g **dot11DSSSOFDMOptionEnabled** management information base (MIB) object for the current PHY type on the 802.11 station.

The **dot11DSSSOFDMOptionEnabled** MIB object specifies whether the current PHY type has enabled the use of the hybrid DSSS-OFDM modulation. When the 802.11 station enables this option, the PHY combines the direct-sequence spread spectrum (DSSS) preamble and header with the orthogonal frequency division multiplexing (OFDM) payload.

For more information about DSSS-OFDM modulation, refer to Clause 19.7 of the IEEE 802.11g-2003 standard.

**Note**  Support for OID\_DOT11\_DSSS\_OFDM\_OPTION \_ENABLED is mandatory if the NIC supports the **dot11\_phy\_type\_erp** PHY type. For more information about how the miniport driver specifies its list of supported PHY types, see [OID\_DOT11\_SUPPORTED\_PHY\_TYPES](oid-dot11-supported-phy-types.md).

 

The data type for OID\_DOT11\_DSSS\_OFDM\_OPTION \_ENABLED is a BOOLEAN value. A value of **TRUE** indicates that the current PHY type has enabled the DSSS-OFDM option.

The **dot11DSSSOFDMOptionEnabled** MIB object is only valid for the Extended-rate PHY (ERP) type. If the current PHY type is not set to dot11\_phy\_type\_erp, the miniport driver must fail the query request by returning NDIS\_STATUS\_INVALID\_DATA from its [*MiniportOidRequest*](https://msdn.microsoft.com/library/windows/hardware/ff559416) function.

If the miniport driver is operating in Extensible Station (ExtSTA) mode, the current PHY type is determined through the ExtSTA **msDot11CurrentPhyID** MIB object. This MIB object specifies the index of the current PHY type within the 802.11 station's list of supported PHY types. For more information about **msDot11CurrentPhyID**, see [OID\_DOT11\_CURRENT\_PHY\_ID](oid-dot11-current-phy-id.md).

**Note**  A Native 802.11 miniport driver that is designed to run on the Windows Vista or Windows Server 2008 operating systems must always reset this 802.11 MIB OID to its default value. This is the case regardless of the value of the **bSetDefaultMIB** member of the DOT11\_RESET\_REQUEST structure. This requirement applies to a miniport driver that, in a call to the **NdisMSetMiniportAttributes** function, sets **MiniportAttributes** -&gt; **Native\_802\_11\_Attributes** -&gt; **Header** -&gt; **Revision** to NDIS\_MINIPORT\_ADAPTER\_802\_11\_ATTRIBUTES\_REVISION\_1.

 

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Version</p></td>
<td><p>Available in Windows Vista and later versions of the Windows operating systems.</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Windot11.h (include Ndis.h)</td>
</tr>
</tbody>
</table>

## See also


[Native 802.11 MIB OIDs](https://msdn.microsoft.com/library/windows/hardware/ff560645)

[Native 802.11 Wireless LAN OIDs](https://msdn.microsoft.com/library/windows/hardware/ff560691)

 

 


--------------------
[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bnetvista\netvista%5D:%20OID_DOT11_DSSS_OFDM_OPTION_ENABLED%20%20RELEASE:%20%288/8/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")

