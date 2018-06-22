---
title: 資格情報 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-security
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- principals [SQL Server], credentials
- schemas [SQL Server], credentials
- permissions [SQL Server], credentials
- groups [SQL Server], credentials
- ALTER ANY CREDENTIAL permission
- security [SQL Server], credentials
- authentication [SQL Server], credentials
- users [SQL Server], credentials
- credentials [SQL Server], about credentials
- credentials [SQL Server]
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
caps.latest.revision: 28
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9de71af86c410658ab37aa1959ab2c9962b30a1c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083609"
---
# <a name="credentials-database-engine"></a>資格情報 (データベース エンジン)
  資格情報は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]外部のリソースへの接続に必要な認証情報 (資格情報) を含むレコードです。 この情報は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]によって内部的に使用されます。 通常、資格情報には Windows ユーザー名とパスワードが含まれます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証経由で接続しているユーザーは、資格情報に格納された情報によって、サーバー インスタンスの外部のリソースにアクセスできるようになります。 外部リソースが Windows である場合、ユーザーは、資格情報に指定されている Windows ユーザーとして認証されます。 1 つの資格情報を複数の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインにマッピングすることもできます。 ただし、1 つの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインは 1 つの資格情報にしかマップできません。  
  
 システム資格情報は、自動的に作成され、特定のエンドポイントに関連付けられます。 システム資格情報の名前は 2 つのシャープ記号 (##) で始まります。  
  
 資格情報の詳細については、次を参照してください。、 [sys.credentials](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql)カタログ ビューです。  
  
## <a name="related-content"></a>関連コンテンツ  
 [資格情報の作成](../authentication-access/create-a-credential.md)[資格情報を作成&#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
 [SQL Server の保護](../securing-sql-server.md)  
  
  
