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
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Properties Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c0b58b301799f2e9d7c7f2366b10419165050b75
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="properties-property-clientnetworkprotocol-class"></a>Properties プロパティ (ClientNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
[Configure Client Protocols (クライアント プロトコルの構成)](http://technet.microsoft.com/library/ms181035.aspx)によって指定された現在のクライアント ネットワーク プロトコルに関連付けられたプロパティを取得します。  
  
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
  
  
