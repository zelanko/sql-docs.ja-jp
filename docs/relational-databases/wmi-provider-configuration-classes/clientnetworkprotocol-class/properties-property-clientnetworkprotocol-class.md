---
title: "Properties プロパティ (ClientNetworkProtocol クラス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Properties Property (ClientNetworkProtocol Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 33c6c8cae3f310113d5bf6d425ca41d2a75d4314
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="properties-property-clientnetworkprotocol-class"></a>Properties プロパティ (ClientNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]によって指定された現在のクライアント ネットワーク プロトコルに関連付けられているプロパティを取得、 [Configure Client Protocols](http://technet.microsoft.com/library/ms181035.aspx)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Properties [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 [クライアントによって使用されるネットワーク プロトコルを表す](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) ClientNetworkProtocol クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 [OrderValue](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) プロパティによって参照される現在のクライアント ネットワーク プロトコルによってサポートされているプロパティを表す **ClientNetworkProtocolProperty クラス** オブジェクトの配列。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [クライアント ネットワーク プロトコルとネットワーク ライブラリの構成](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
