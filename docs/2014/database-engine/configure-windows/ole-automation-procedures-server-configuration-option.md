---
title: Ole Automation Procedures サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d34615ce1f808c1015c9c3d312a38a67dba291b4
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935193"
---
# <a name="ole-automation-procedures-server-configuration-option"></a>Ole Automation Procedures サーバー構成オプション
  `Ole Automation Procedures` オプションは、[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ内で OLE オートメーション オブジェクトをインスタンス化するかどうかを指定するために使用します。 このオプションは、ポリシー ベースの管理または **sp_configure** ストアド プロシージャを使用して構成することもできます。 詳細については、「 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)」を参照してください。  
  
 `Ole Automation Procedures` オプションに設定できる値を次に示します。  
  
 0  
 OLE オートメーション プロシージャを無効にします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の新しいインスタンスの既定値です。  
  
 1  
 OLE オートメーション プロシージャを有効にします。  
  
 OLE オートメーション プロシージャが有効である場合、 **sp_OACreate** を呼び出すと OLE 共有実行環境が開始します。  
  
 オプションの現在の値を `Ole Automation Procedures` 表示および変更するには、 **sp_configure**システムストアドプロシージャを使用します。  
  
## <a name="examples"></a>例  
 OLE オートメーション プロシージャの現在の設定を確認する方法を次の例に示します。  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 OLE オートメーション プロシージャを有効にする方法を次の例に示します。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [セキュリティ構成](../../relational-databases/security/surface-area-configuration.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
