---
title: SqlServerAlias クラス
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- SqlServerAlias Class
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 613df198c6278c43fce8de71c831aa017a82bcea
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85888432"
---
# <a name="sqlserveralias-class"></a>SqlServerAlias クラス
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  [SqlServerAlias class](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md)クラスは、サーバー接続の別名を表します。  
  
 サーバー接続別名は、次の両方に該当する場合に必要となります。  
  
-   クライアントが、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 既定のネットワーク転送ではないネットワークトランスポート経由でのインスタンスに接続しています。  
  
-   クライアントが接続されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスが代替の名前付きパイプをリッスンする場合。  
  
 **注:**[SqlServerAlias クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md)は、プロバイダークラスから**Put**メソッドを継承します。 ただし、**プロバイダー::P ut**メソッドによって示される結果は返されません。 詳細については、WMI のドキュメントを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [クライアント プロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
