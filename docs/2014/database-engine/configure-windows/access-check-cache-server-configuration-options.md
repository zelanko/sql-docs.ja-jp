---
title: access check cache サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
- access check cache bucket count
- access check cache quota
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feed895eeb7b11b4c41c51c4c26859a1057d2733
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86158760"
---
# <a name="access-check-cache-server-configuration-options"></a>access check cache サーバー構成オプション
データベース オブジェクトに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からアクセスすると、アクセス チェックが **access check result cache**と呼ばれる内部構造にキャッシュされます。 
  
**Access check cache バケット数**オプションは、アクセスチェックの結果キャッシュに使用されるハッシュバケットの数を制御します。 

**Access check cache quota**オプションは、アクセスチェックの結果キャッシュに格納されるエントリの数を制御します。 エントリの最大数に達すると、アクセスチェックの結果キャッシュから最も古いエントリが削除されます。
  
既定値は 0 で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がこれらのオプションを管理していることを示します。 から [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 、既定値は次の内部構成に変換されます。
-   アクセス確認キャッシュバケット数の場合、値0は x86 アーキテクチャの場合は256バケット、x64 と IA-64 アーキテクチャの場合は2048バケットの既定値を設定します。
-   アクセス確認キャッシュクォータの場合、値0は、x86 アーキテクチャの場合は1024エントリ、x64 と IA-64 アーキテクチャの場合は28192048バケットの既定値を設定します。

まれに、これらのオプションを変更することによってパフォーマンスが向上する場合があります。 たとえば、使用されているメモリが多すぎる場合は、アクセスチェックの結果キャッシュのサイズを小さくすることができます。 または、アクセス許可の再計算時に高い CPU 使用率が発生した場合は、アクセスチェックの結果キャッシュのサイズを大きくすることもできます。

> [!IMPORTANT]
> これらのオプションはマイクロソフト カスタマー サポート サービスから指示があった場合にのみ変更することをお勧めします。
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
