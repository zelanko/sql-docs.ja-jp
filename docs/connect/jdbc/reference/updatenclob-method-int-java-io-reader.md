---
title: updateNClob (int, java.io.Reader) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 17adafd4-3ac3-4ff0-af9d-f087cc5ef936
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7f78bcff36f64337d782ab7ad18105bfaa3c4ce0
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903102"
---
# <a name="updatenclob-method-int-javaioreader"></a>updateNClob (int, java.io.Reader) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された **Reader** オブジェクトを使用して、指定された列を更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateNClob(int columnIndex,  
                        java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 列インデックスを示す **int** です。  
  
 *reader*  
  
 Reader オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateNClob メソッドは、java.sql.ResultSet インターフェイスの updateNClob メソッドで規定されています。  
  
 このメソッドは、**nvarchar(max)** 、**ntext**、および **xml** 列でのみサポートされています。 このメソッドを他のデータ型で使用すると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [updateNClob メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
