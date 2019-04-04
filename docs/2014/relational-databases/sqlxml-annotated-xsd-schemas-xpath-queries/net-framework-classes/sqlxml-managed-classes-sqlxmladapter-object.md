---
title: SqlXmlAdapter オブジェクト (SQLXML マネージ クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6764b729ffb2a917a03332d8472053e590d5f352
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52790144"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a>SqlXmlAdapter オブジェクト (SQLXML マネージド クラス)
  このオブジェクトでは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework のデータセットとの対話を容易にするためのメソッドが提供されます。 実際のサンプルでは、[.NET 環境での SQLXML 機能へのアクセス](accessing-sqlxml-functionality-in-the-net-environment.md)を参照してください。  
  
 SqlXmlAdapter オブジェクトには、これらのメソッドがサポートされています。  
  
 void Fill (DataSet ds)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から取得した XML データを .NET Framework のデータセットに格納します。  
  
 void Update (DataSet ds)  
 データセットのデータから、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のレコードを更新します。  
  
 SqlXmlAdapter オブジェクトには、これらのコンス トラクターがサポートされています。  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a>参照  
 [SqlXmlCommand オブジェクト&#40;SQLXML マネージ クラス&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)   
 [SqlXmlParameter オブジェクト&#40;SQLXML マネージ クラス&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
