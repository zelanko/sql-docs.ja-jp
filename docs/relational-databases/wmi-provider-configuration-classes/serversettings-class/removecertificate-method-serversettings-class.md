---
title: RemoveCertificate メソッド (ServerSettings)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- RemoveCertificate Method (ServerSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 9ffdbc39-93f5-48fb-859a-86a3ad545827
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0bdbdd4bde2436eb11962790e65bb65daa938500
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85880756"
---
# <a name="removecertificate-method-serversettings-class"></a>RemoveCertificate メソッド (ServerSettings クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスから現在のセキュリティ証明書を削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.RemoveCertificate()  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 [のインスタンス上のサーバー設定を表す](../../../relational-databases/wmi-provider-configuration-classes/serversettings-class/serversettings-class.md) ServerSettings クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 U**int32**値。サービスが正常に変更された場合は0、要求がサポートされていない場合は1になり、それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
