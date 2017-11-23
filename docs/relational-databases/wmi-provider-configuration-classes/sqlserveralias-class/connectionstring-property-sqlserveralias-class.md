---
title: "ConnectionString プロパティ (SqlServerAlias クラス) |Microsoft ドキュメント"
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
apiname: ConnectionString Property (SqlServerAlias Class)
apilocation: sqlmgmproviderxpsp2up.mof
helpviewer_keywords: ConnectionString property
ms.assetid: 8a3692b9-3a34-42e2-b0b9-28e6bd3a7aba
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 674966101fe0b0290f4cb95dcf8353e5c6228ac5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="connectionstring-property-sqlserveralias-class"></a>ConnectionString プロパティ (SqlServerAlias クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]サーバー接続別名の接続を確立するために使用される接続文字列を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.ConnectionString [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 [の別名を表す](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) SqlServerAlias クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サーバー接続別名に対応する接続を確立するために使用される接続文字列を指定する文字列。  
  
## <a name="remarks"></a>解説  
  
