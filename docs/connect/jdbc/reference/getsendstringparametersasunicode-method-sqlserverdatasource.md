---
title: getSendStringParametersAsUnicode メソッド (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3836d0ab-c3fb-41ff-bb89-10389594ae51
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b54715e0eb4e813c65b0ea9cf750bc07388d291d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80929181"
---
# <a name="getsendstringparametersasunicode-method-sqlserverdatasource"></a>getSendStringParametersAsUnicode メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  サーバーへの文字列パラメーターの UNICODE 形式による送信が有効になっているかどうかを示す **boolean** 値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getSendStringParametersAsUnicode()  
```  
  
## <a name="return-value"></a>戻り値  
 サーバーに文字列パラメーターが UNICODE 形式で送信される場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 sendStringParametersAsUnicode プロパティが **true** (既定値) に設定されている場合、文字列パラメーターは、UNICODE 形式でサーバーに送信されます。 sendStringParametersAsUnicode が **false** に設定されている場合、UNICODE ではなく ASCII/MBCS 形式で、文字列パラメーターがサーバーに送信されます。 sendStringParametersAsUnicode が設定されていない場合、getSendStringParametersAsUnicode は既定値の **true** を返します。  
  
 sendStringParametersAsUnicode 接続プロパティについて詳しくは、「[接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
