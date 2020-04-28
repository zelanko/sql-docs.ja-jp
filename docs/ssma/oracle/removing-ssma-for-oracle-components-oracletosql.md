---
title: SSMA for Oracle コンポーネントの削除 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Uninstalling the Extension Pack
ms.assetid: 8b527a56-4e52-487a-9ac9-2320388e6d7d
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 0434f88c46d14672c84f5f7939488a827b229e27
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68266560"
---
# <a name="removing-ssma--for-oracle-components-oracletosql"></a>SSMA for Oracle コンポーネントの削除 (OracleToSQL)
Oracle からへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータベースの移行が完了したら、ssma コンポーネントのアンインストールが必要になる場合があります。 クライアントコンポーネントはいつでもアンインストールできます。 ただし、移行したデータベースで**sysdb**データベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の**ssma_oracle**スキーマの関数が使用されなくなっていない限り、から拡張パックをアンインストールしないでください。  
  
## <a name="uninstalling-the-ssma-for-oracle-client"></a>SSMA for Oracle クライアントのアンインストール  
SSMA をアンインストールするには、[**プログラムの追加と削除**] を使用します。  
  
**SSMA をアンインストールするには**  
  
1.  [コントロール] パネルで **[プログラムの追加と削除]** を開きます。  
  
2.  [ ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle] の [Migration Assistant**] を選択し、[**削除**] をクリックします。  
  
3.  SSMA をアンインストールすることを確認するには、[**はい**] をクリックします。  
  
## <a name="uninstalling-the-extension-pack"></a>拡張機能パックのアンインストール  
移行したデータベースで**ssma_oracle**スキーマのオブジェクトが使用されていないことが確実な場合は、[**プログラムの追加と削除**] を使用して拡張機能パックを削除できます。  
  
**拡張機能パックをアンインストールするには**  
  
1.  [コントロール] パネルで **[プログラムの追加と削除]** を開きます。  
  
2.  [ **Oracle Extension Pack] の [Microsoft SQL Server Migration Assistant**] を選択し、[**削除**] をクリックします。  
  
3.  拡張パックをアンインストールすることを確認するには、[**はい**] をクリックします。  
  
4.  [ユーティリティを使用したインスタンスデータベーススクリプト] ページで、インスタンスを選択し、[**次へ**] をクリックします。  
  
5.  [接続パラメーター] ページで、認証方法を選択し、[**次へ**] をクリックします。  
  
    Windows 認証では、Windows 資格情報を使用しての[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスにログオンしようとします。 [認証] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を選択した場合は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ログイン名とパスワードを入力する必要があります。  
  
6.  [操作が完了しました] ページで、[ **OK]** をクリックします。  
  
7.  [完了] ページで、[**終了**] をクリックします。  
  
アンインストール後、を使用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]して、 **ssma_oracle**スキーマのオブジェクトと、場合によっては**sysdb**データベース全体が削除されたことを確認できます。 ただし、他の SSMA 製品を使用する場合は、 **sysdb**データベースも使用します。 データベースが存在し、他のデータベースがこのデータベース内のオブジェクトを参照していない場合は、データベースをデタッチできます。  
  
## <a name="see-also"></a>参照  
[SSMA for Oracle Client &#40;OracleToSQL&#41;のインストール](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[SQL Server &#40;OracleToSQL&#41;での SSMA コンポーネントのインストール](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
  
