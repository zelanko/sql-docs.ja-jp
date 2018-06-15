---
title: コマンド (ADO - WFC 構文) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Command collection [ADO], ADO/WFC syntax
ms.assetid: 39d0aa06-03ac-4c9a-8400-83947756ef99
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c57cd9a65cdbf3662f7ed7499d979753d9ecd0b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276611"
---
# <a name="command-ado---wfc-syntax"></a>コマンド (ADO - WFC 構文)
## <a name="package-commswfcdata"></a>パッケージ com.ms.wfc.data  
  
### <a name="constructor"></a>コンス トラクター  
  
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
  
 **ExecuteUpdate**メソッドは、特殊なケース メソッドを呼び出す、基になる ADO**実行**特定のパラメーターを持つメソッドです。 **ExecuteUpdate**メソッドの戻り値をサポートしていません、 **Recordset**オブジェクト、ため、**実行**メソッドの*オプション*パラメーターは、使用して変更**AdoEnums.ExecuteOptions.NORECORDS**です。 後に、**実行**メソッド完了すると、その更新された*RecordsAffected*にパラメーターが渡される、 **executeUpdate** として最後に返されるメソッド**int**です。  
  
### <a name="properties"></a>[プロパティ]  
  
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
