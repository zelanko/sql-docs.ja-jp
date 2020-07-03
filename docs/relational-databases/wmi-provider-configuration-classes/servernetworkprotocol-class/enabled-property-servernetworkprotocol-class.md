---
title: Enabled プロパティ (ServerNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Enabled Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Enabled property
ms.assetid: a514822a-91f1-4aca-9175-2b96cff29700
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 755ef436a63a421fa2ee7ffaa335dee452d40d8b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85888815"
---
# <a name="enabled-property-servernetworkprotocol-class"></a>Enabled プロパティ (ServerNetworkProtocol クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  サーバー ネットワーク プロトコルが有効かどうかを指定するブール型のプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Enabled [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 のインスタンスによって使用されるネットワークプロトコルを表す[Servernetworkprotocol クラス](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サーバーネットワークプロトコルが有効かどうかを指定するブール値です。サーバーネットワークプロトコルが有効になっている場合は**true** 、サーバーネットワークプロトコルが無効になっている場合は**false**です。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
