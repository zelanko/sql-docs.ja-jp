---
title: ServerName プロパティ (SqlServerAlias クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- ServerName Property (SqlServerAlias Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ServerName property
ms.assetid: 58c82b19-b548-42fa-9c5a-059b606da097
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5319f26db7b54fa6bb5bcae73068c7f11e17362d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47768380"
---
# <a name="servername-property-sqlserveralias-class"></a>ServerName プロパティ (SqlServerAlias クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  インスタンスの名前を取得[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サーバー接続別名によって指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.ServerName [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 [の別名を表す](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) SqlServerAlias クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サーバー接続別名によって参照された [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの名前を指定する文字列値。  
  
## <a name="remarks"></a>コメント  
  
