---
title: XML システム ストアド プロシージャ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7673efc55f780f0ebd99da740c54ea4787b40260
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215192"
---
# <a name="xml-system-stored-procedures"></a>XML システム ストアド プロシージャ
  SQL Server には、OPENXML と共に使用する、次のシステム ストアド プロシージャが用意されています。  
  
-   [sp_xml_preparedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql)  
  
-   [sp_xml_removedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql)  
  
 OPENXML を使用してクエリを作成するには、最初に **sp_xml_preparedocument**を呼び出して XML ドキュメントの内部表現を作成する必要があります。 このストアド プロシージャは、XML ドキュメントの内部表現へのハンドルを返します。 その後、このハンドルは OPENXML に渡されます。 OPENXML は、XPath を基にドキュメントの行セット ビューを提供します。 具体的には、これは 1 つの行パターンと 1 つ以上の列パターンで構成されます。  
  
> [!NOTE]  
>  **sp_xml_preparedocument** から返されたドキュメント ハンドルは、セッションが確立されている間のみ有効です。  
  
 XML ドキュメントの内部表現は、 **sp_xml_removedocument** システム ストアド プロシージャを呼び出すことによってメモリから削除できます。  
  
## <a name="see-also"></a>参照  
 [OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql)   
 [OPENXML &#40;SQL Server&#41;](../xml/openxml-sql-server.md)  
  
  
