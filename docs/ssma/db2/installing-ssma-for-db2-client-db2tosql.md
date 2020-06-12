---
title: SSMA for DB2 クライアントのインストール (DB2ToSQL) |Microsoft Docs
description: DB2 クライアント用の SQL Server Migration Assistant (SSMA) とのインストールの前提条件について説明します。
ms.prod: sql
ms.custom: ''
ms.date: 09/07/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7615f775a43da2853a0c98f8402f738e73dc8bb6
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293809"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>SSMA for DB2 クライアントのインストール (DB2ToSQL)

SSMA クライアントは、次のタスクを実行するプログラムファイルで構成されています。  
  
- DB2 データベースに接続します。  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する。  
  
- DB2 データベースオブジェクトを構文に変換 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。  
  
- オブジェクトをに読み込み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
- データをに移行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。  
  
このトピックでは、SSMA のインストールの前提条件と手順について説明します。  
  
## <a name="prerequisites"></a>前提条件

SSMA は、for z/OS バージョン9.0 および10.0 または DB2 on LUW バージョン9.8 および10.1 以降のバージョンおよび2012以降のバージョンで動作するように設計されてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
SSMA をインストールする前に、コンピューターが次の要件を満たしていることを確認してください。  
  
- Windows 7 以降のバージョン、または Windows Server 2008 以降のバージョン。  
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー3.1 以降のバージョン。  
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] バージョン4.0 以降のバージョン。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)]バージョン4.0 は、製品メディアで入手でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 また、 [.NET Framework デベロッパーセンター](https://go.microsoft.com/fwlink/?LinkId=48882)から入手することもできます。  
  
- Microsoft OLEDB Provider for DB2 version 5 以降のバージョン、および移行する DB2 データベースへの接続。  
  
- にアクセスし、データベースオブジェクトとデータの移行先となる、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB のターゲットインスタンスをホストするコンピューターに対して十分なアクセス許可を付与します。 詳細については、「 [SQL Server &#40;DB2eToSQL&#41;への接続](../../ssma/db2/connecting-to-sql-server-db2etosql.md)」を参照してください。  
  
- 4 GB の RAM を推奨します。  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Microsoft OLEDB Provider for DB2  

DB2 バージョン6.0 の OLEDB プロバイダーをダウンロードするには、 [Microsoft® SQL Server® 2017 Feature Pack](https://www.microsoft.com/download/details.aspx?id=55992)」を参照してください。

SSMA は Web からダウンロードできます。 最新バージョンをダウンロードするには、 [SQL Server Migration Assistant のダウンロードページ](https://aka.ms/ssmafordb2)を参照してください。  
  
最新バージョンをダウンロードしたら、SSMA をインストールできるようにインストールファイルを抽出します。  
  
SSMA クライアントをインストールするには:
  
1. SSMA for DB2 *n*.Install.exe をダブルクリックします。ここで、 *n*はビルド番号です。  
  
2. **[ようこそ]** ページで **[次へ]** をクリックします。  
  
   前提条件がインストールされていない場合は、最初に必要なコンポーネントをインストールする必要があることを示すメッセージが表示されます。 すべての前提条件がインストールされていることを確認してから、インストールプログラムを再実行してください。  
  
3. 使用許諾契約書を確認します。 同意する場合は、[**使用許諾契約書に同意**します] を選択し、[**次へ**] を選択します。  
  
4. [**セットアップの種類の選択**] ページで、[**標準**] を選択します。  
  
5. **[インストール]** を選択します。  
  
> [!IMPORTANT]  
> 新しいバージョンをインストールする前に、SSMA for DB2 の以前のバージョンをすべてアンインストールしてください。
  
既定のインストール場所は、DB2 の場合は C:\Program の SQL Server Migration Assistant です。  
  
## <a name="see-also"></a>関連項目

[SQL Server &#40;DB2ToSQL&#41;での SSMA コンポーネントのインストール](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[DB2 データベースを SQL Server &#40;DB2ToSQL&#41;に移行する](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
