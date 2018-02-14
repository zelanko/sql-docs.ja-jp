---
title: "XML システム ストアド プロシージャ | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 44e9f0a98ed9238a8c914aa0a5f696fe5a5942e5
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="xml-system-stored-procedures"></a>XML システム ストアド プロシージャ
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
SQL Server には、OPENXML と共に使用する、次のシステム ストアド プロシージャが用意されています。  
  
-   [sp_xml_preparedocument &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql.md)  
  
-   [sp_xml_removedocument &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql.md)  
  
 OPENXML を使用してクエリを作成するには、最初に **sp_xml_preparedocument**を呼び出して XML ドキュメントの内部表現を作成する必要があります。 このストアド プロシージャは、XML ドキュメントの内部表現へのハンドルを返します。 その後、このハンドルは OPENXML に渡されます。 OPENXML は、XPath を基にドキュメントの行セット ビューを提供します。 具体的には、これは 1 つの行パターンと 1 つ以上の列パターンで構成されます。  
  
> [!NOTE]  
>  **sp_xml_preparedocument** から返されたドキュメント ハンドルは、セッションが確立されている間のみ有効です。  
  
 XML ドキュメントの内部表現は、 **sp_xml_removedocument** システム ストアド プロシージャを呼び出すことによってメモリから削除できます。  
  
## <a name="see-also"></a>参照  
 [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md)   
 [OPENXML &#40;SQL Server&#41;](../../relational-databases/xml/openxml-sql-server.md)  
  
  
