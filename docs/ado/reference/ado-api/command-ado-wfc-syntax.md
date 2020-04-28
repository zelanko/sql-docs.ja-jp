---
title: Command (ADO-WFC 構文) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Command collection [ADO], ADO/WFC syntax
ms.assetid: 39d0aa06-03ac-4c9a-8400-83947756ef99
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4722316cc92567000294c57089afd8840bea1bcd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67919822"
---
# <a name="command-ado---wfc-syntax"></a>Command (ADO - WFC 構文)
## <a name="package-commswfcdata"></a>パッケージ com.. wfc. データ  
  
### <a name="constructor"></a>Constructor  
  
```  
public Command()  
public Command(String commandtext)  
```  
  
### <a name="methods"></a>メソッド  
  
```  
public void cancel()  
public com.ms.wfc.data.Parameter createParameter(String  
    Name, int Type, int Direction, int Size, Object Value)  
public Recordset execute()  
public Recordset execute(Object[] parameters)  
public Recordset execute(Object[] parameters, int options)  
public int executeUpdate(Object[] parameters)  
public int executeUpdate(Object[] parameters, int options)  
public int executeUpdate()  
```  
  
 **Executeupdate**メソッドは、特定のパラメーターを使用して基になる ADO **execute**メソッドを呼び出す特殊なケースメソッドです。 **Executeupdate**メソッドでは、**レコードセット**オブジェクトの戻りがサポートされていないため、 **execute**メソッドの*options*パラメーターは AdoEnums を使用して変更されます。 **NORECORDS**。 **Execute**メソッドが完了すると、更新された*RecordsAffected*パラメーターが**executeupdate**メソッドに戻されます。このメソッドは、最後に**int**として返されます。  
  
### <a name="properties"></a>Properties  
  
```  
public com.ms.wfc.data.Connection getActiveConnection()  
public void setActiveConnection(com.ms.wfc.data.Connection con)  
public void setActiveConnection(String conString)  
public String getCommandText()  
public void setCommandText(String command)  
public int getCommandTimeout()  
public void setCommandTimeout(int timeout)  
public int getCommandType()  
public void setCommandType(int type)  
public String getName()  
public void setName(String name)  
public boolean getPrepared()  
public void setPrepared(boolean prepared)  
public int getState()  
public com.ms.wfc.data.Parameter getParameter(int n)  
public com.ms.wfc.data.Parameter getParameter(String n)  
public com.ms.wfc.data.Parameters getParameters()  
public AdoProperties getProperties()  
```  
  
## <a name="see-also"></a>参照  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
