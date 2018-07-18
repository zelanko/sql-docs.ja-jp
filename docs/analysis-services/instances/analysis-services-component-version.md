---
title: SQL Server Analysis Services 累積更新プログラムのビルド バージョンを確認します |。Microsoft Docs
ms.date: 07/11/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b1da8384bb51360178e1735d13f6c6b706e8b7ff
ms.sourcegitcommit: 87efa581f7d4d84e9e5c05690ee1cb43bd4532dc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38999355"
---
# <a name="verify-analysis-services-cumulative-update-build-version"></a>Analysis Services 累積更新プログラムのビルド バージョンを確認します。

SQL Server 2017 以降では、Analysis Services のビルド バージョン番号と SQL Server データベース エンジンのビルド バージョン番号が一致しません。 Analysis Services とデータベース エンジンの両方で同じインストーラーを使用して、ビルド システムごとの使用は区別されます。

 場合によっては、累積的な更新プログラム (CU) のビルド パッケージが適用されているかどうか、および Analysis Services のコンポーネントが更新されていることを確認する必要があります。 Analysis Services コンポーネントのファイルが特定の CU のビルドのバージョン番号を持つコンピューターにインストールのビルド バージョン番号を比較することで確認できます。

## <a name="verify-component-file-version"></a>コンポーネント ファイルのバージョンを確認します。

コンポーネント ファイルのバージョンを確認するには 

1. 移動して[SQL Server 2017 のビルド バージョン](https://support.microsoft.com/help/4047329)します。 
2. **SQL Server 2017 の累積更新プログラム (CU) ビルド**、 をクリックして、**サポート技術情報番号**を確認するビルドします。
3. **For SQL Server 2017 の累積的な更新 (#)** 記事で、**パッケージ情報の累積的な更新**セクションで、展開**累積更新プログラム パッケージのファイル情報**.
4. **SQL Server 2017 Analysis Services**テーブル、ファイルのバージョンを確認してください、 **msmdsrv.exe**コンポーネント ファイル。 CU が適用されている場合、ファイルのバージョン番号は、コンピューターにインストールされている msmdsrv.exe ファイルと一致する必要があります。

## <a name="see-also"></a>参照  

[SQL Server サービス更新プログラムのインストール](../../database-engine/install-windows/install-sql-server-servicing-updates.md)  

[Microsoft SQL Server の update Center](https://msdn.microsoft.com/library/ff803383.aspx)
  
  
