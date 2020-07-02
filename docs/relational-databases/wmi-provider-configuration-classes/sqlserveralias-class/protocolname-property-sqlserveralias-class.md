---
title: ProtocolName プロパティ (SqlServerAlias)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolName Property (SqlServerAlias Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolName property
ms.assetid: 8fb81ab3-15f1-4a71-be72-2072c6bcc670
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 22a37f9d1c3e02b2bd4c61dab5ea8f053cd1dd57
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85753740"
---
# <a name="protocolname-property-sqlserveralias-class"></a>ProtocolName プロパティ (SqlServerAlias クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  サーバー接続別名によって使用されるプロトコルの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.ProtocolName [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 [の別名を表す](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) SqlServerAlias クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サーバー接続別名によって使用されるプロトコルの名前を指定する文字列値。  
  
## <a name="remarks"></a>Remarks  
  
