---
title: "IpAddresses プロパティ (ServerNetworkProtocol クラス) |Microsoft ドキュメント"
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
apiname: IpAddresses Property (ServerNetworkProtocol Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: IpAddresses property
ms.assetid: e5d66f7e-9719-436e-b723-12d56f914a05
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4aad0f209fd32d71371bed19a4cfc93c872bfbb5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a>IpAddresses プロパティ (ServerNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]サーバー ネットワーク プロトコルに関連付けられている IP アドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.IpAddresses [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 A **ServerNetworkProtocol**のインスタンスによって使用されるネットワーク プロトコルを表すオブジェクト[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 配列[ServerNetworkProtocolIPAdress クラス](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md)サーバー ネットワーク プロトコルによってサポートされる IP アドレスを表すオブジェクト。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
