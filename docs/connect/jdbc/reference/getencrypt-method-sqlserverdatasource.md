---
title: getEncrypt メソッド (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 031c56f7389fef6afefd2e0b61e07117fce0b6d5
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924950"
---
# <a name="getencrypt-method-sqlserverdatasource"></a>getEncrypt メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  encrypt プロパティが有効であるかどうかを示す **Boolean** 値が返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>戻り値  
 encrypt プロパティが有効である場合は、**true** です。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 encrypt プロパティが **true** に設定されている場合、サーバーに証明書がインストールされていれば、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] によって、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で SSL 暗号化が確実に使用されるようになります。暗号化の対象となるのは、サーバーとクライアントの間で送信されるすべてのデータです。  
  
 encrypt プロパティが指定されていないか、または **false** に設定されている場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がドライバーによって SSL 暗号化のサポートを強制されることはありません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスが SSL 暗号化を強制的に使用するように構成されていない場合、接続は暗号化なしで確立されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスが SSL 暗号化を強制的に使用するように構成されている場合、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] は、使用中の Java 仮想マシン (JVM) が正常に構成されていれば自動的に SSL 暗号化を有効にし、そうでなければ接続を終了してエラーを生成します。 暗号化プロパティが設定されていない場合、[getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md) メソッドは既定値の **false** が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
