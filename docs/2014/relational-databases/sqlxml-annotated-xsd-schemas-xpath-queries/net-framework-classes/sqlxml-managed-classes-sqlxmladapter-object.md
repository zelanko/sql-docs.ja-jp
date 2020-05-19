---
title: SqlXmlAdapter オブジェクト (SQLXML マネージクラス) |Microsoft Docs
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 86231096c8eef084b36d6195a1c720bd4f9038a3
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717956"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a>SqlXmlAdapter オブジェクト (SQLXML マネージド クラス)
  このオブジェクトでは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework のデータセットとの対話を容易にするためのメソッドが提供されます。 実際のサンプルについては、「 [.Net 環境での SQLXML 機能へのアクセス](accessing-sqlxml-functionality-in-the-net-environment.md)」を参照してください。  
  
 SqlXmlAdapter オブジェクトは、次のメソッドをサポートしています。  
  
 void の Fill (DataSet ds)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から取得した XML データを .NET Framework のデータセットに格納します。  
  
 void 更新 (データセット ds)  
 データセットのデータから、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のレコードを更新します。  
  
 SqlXmlAdapter オブジェクトは、次のコンストラクターをサポートしています。  
  
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
 [SqlXmlCommand オブジェクト &#40;SQLXML マネージクラス&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)   
 [SqlXmlParameter オブジェクト &#40;SQLXML マネージクラス&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
