---
title: "強力なパスワード | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e58e590b2b57c96a18b8752b33d7b559b375d028
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="strong-passwords"></a>強力なパスワード
  パスワードは、サーバーのセキュリティ上で最も弱点になる可能性があります。 パスワードを選択するときは、常に最大限の注意が必要です。 強力なパスワードの特徴は次のとおりです。  
  
-   8 文字以上である  
  
-   文字、数字、および記号を組み合わせたパスワードである  
  
-   辞書に載っていない  
  
-   コマンド名ではない  
  
-   人名ではない  
  
-   ユーザー名ではない  
  
-   コンピューター名ではない  
  
-   定期的に変更される  
  
-   以前のパスワードと明らかに異なる  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のパスワードには、文字、記号、および数字を使用し、最大 128 文字まで含めることができます。 ログイン、ユーザー名、ロール、およびパスワードは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用されることが多く、特定の記号については二重引用符 (") または角かっこ ([ ]) で囲む必要が生じます。 これらの区切り記号を [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用するのは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン、ユーザー、ロール、またはパスワードに次のような特徴がある場合です。  
  
-   スペースが含まれているか、スペースが先頭にある  
  
-   $ または @ で始まる  
  
 OLE DB または ODBC の接続文字列で使用する場合、ログインまたはパスワードの文字に、[] {}() , ; ? * ! @ は含めないでください。 * ! @。 これらの文字は、接続の初期化や、接続の値を区切る場合に使用されています。  
  
## <a name="related-content"></a>関連コンテンツ  
 [パスワード ポリシー](../../relational-databases/security/password-policy.md)  
  
  

