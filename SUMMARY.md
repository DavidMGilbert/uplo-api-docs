# Table of contents

* [Introduction](README.md)
* [Documentation Standards](introduction/documentation-standards.md)

## Standard Responses
* [Success Response](standard-responses/success-response.md)
* [Error Response](standard-responses/error-response.md)

## Authentication
* [Authentication](authentication/authentication.md)

## Units
* [Units](units/units.md)

## Environment Variables
* [Environment Variables](environment-variables/environment-variables.md)

## Consensus
* [/consensus [GET]](consensus/consensus-get.md)
* [/consensus/blocks [GET]](consensus/consensus-blocks-get.md)
* [/consensus/subscribe/:id [GET]](consensus/consensus-subscribe-id-get.md)
* [/consensus/validate/transactionset [POST]](consensus/consensus-validate-transactionset-post.md)

## Daemon
* [/daemon/alerts [GET]](daemon/daemon-alerts-get.md)
* [/daemon/constants [GET]](daemon/daemon-constants-get.md)
* [/daemon/settings [GET]](daemon/daemon-settings-get.md)
* [/daemon/settings [POST]](daemon/daemon-settings-post.md)
* [/daemon/stack [GET]](daemon/daemon-stack-get.md)
* [/daemon/stop [GET]](daemon/daemon-stop-get.md)
* [/daemon/update [GET]](daemon/daemon-update-get.md)
* [/daemon/update [POST]](daemon/daemon-update-post.md)
* [/daemon/version [GET]](daemon/daemon-version-get.md)

## FeeManager
* [/feemanager [GET]](feemanager/feemanager-get.md)
* [/feemanager/add [POST]](feemanager/feemanager-add-post.md)
* [/feemanager/cancel [POST]](feemanager/feemanager-cancel-post.md)
* [/feemanager/paidfees [GET]](feemanager/feemanager-paidfees-get.md)
* [/feemanager/pendingfees [GET]](feemanager/feemanager-pendingfees-get.md)

## Gateway
* [/gateway [GET]](gateway/gateway-get.md)
* [/gateway [POST]](gateway/gateway-post.md)
* [/gateway/bandwidth [GET]](gateway/gateway-bandwidth-get.md)
* [/gateway/conect/:netaddress [POST]](gateway/gateway-connect-netaddress-post.md)
* [/gateway/disconnect/:netaddress [POST]](gateway/gateway-disconnect-netaddress-post.md)
* [/gateway/blocklist [GET]](gateway/gateway-blocklist-get.md)
* [/gateway/blocklist [POST]](gateway/gateway-blocklist-post.md)

## Host
* [/host [GET]](host/host-get.md)
* [/host [POST]](host/host-post.md)
* [/host/bandwidth [GET]](host/host-bandwidth-get.md)
* [/host/announce [POST]](host/host-announce-post.md)
* [/host/contracts [GET]](host/host-contracts-get.md)
* [/host/storage [GET]](host/host-storage-get.md)
* [/host/storage/folders/add [POST]](host/host-storage-folders-add-post.md)
* [/host/storage/folders/remove [POST]](host/host-storage-folders-remove-post.md)
* [/host/storage/folders/resize [POST]](host/host-storage-folders-resize-post.md)
* [/host/storage/sectors/delete/:merkleroot [POST]](host/host-storage-sectors-delete-merkleroot-post.md)
* [/host/edtimatescore [GET]](host/host-estimatescore-get.md)

## HostDB
* [/hostdb [GET]](hostdb/hostdb-get.md)
* [/hostdb/active [GET]](hostdb/hostdb-active-get.md)
* [/hostdb/all [GET]](hostdb/hostdb-all-get.md)
* [/hostdb/hosts/:pubkey [GET]](hostdb/hostdb-hosts-pubkey-get.md)
* [/hostdb/filtermode [GET]](hostdb/hostdb-filtermode-get.md)
* [/hostdb/filtermode [POST]](hostdb/hostdb-filtermode-post.md)

## Miner
* [/miner [GET]](miner/miner-get.md)
* [/miner/start [GET]](miner/miner-start-get.md)
* [/miner/stop [GET]](miner/miner-stop-get.md)
* [/miner/block [POST]](miner/miner-block-post.md)
* [/miner/header [GET]](miner/miner-header-get.md)
* [/miner/header [POST]](miner/miner-header-post.md)

## Renter
* [/renter [GET]](renter/renter-get.md)
* [/renter [POST]](renter/renter-post.md)
* [/renter/allowance/cancel [POST]](renter/renter-allowance-cancel-post.md)
* [/renter/clean [POST]](renter/renter-clean-post.md)
* [/renter/contract/cancel [POST]](renter/renter-contract-cancel-post.md)
* [/renter/backup [POST]](renter/renter-backup-post.md)
* [/renter/recoverbackup [POST]](renter/renter-recoverbackup-post.md)
* [/renter/uploadedbackups [POST]](renter/renter-uploadedbackups-post.md)
* [/renter/contracts [GET]](renter/renter-contracts-get.md)
* [/renter/contractstatus [GET]](renter/renter-contractstatus-get.md)
* [/renter/contractorchurnstatus [GET]](renter/renter-contractorchurnstatus-get.md)
* [/renter/setmaxperiodchurn [POST]](renter/renter-setmaxperiodchurn-post.md)
* [/renter/dir/uplopath [GET]](renter/renter-dir-uplopath-get.md)
* [/renter/dir/uplopath [POST]](renter/renter-dir-uplopath-post.md)
* [/renter/downloadinfo/uid [GET]](renter/renter-downloadinfo-uid-get.md)
* [/renter/downloads [GET]](renter/renter-downloads-get.md)
* [/renter/downloads/clear [POST]](renter/renter-downloads-clear-post.md)
* [/renter/prices [GET]](renter/renter-prices-get.md)
* [/renter/files [GET]](renter/renter-files-get.md)
* [/renter/file/uplopath [GET]](renter/renter-file-uplopath-get.md)
* [/renter/file/uplopath [POST]](renter/renter-file-uplopath-post.md)
* [/renter/file/delete/uplopath [POST]](renter/renter-file-delete-uplopath-post.md)
* [/renter/downloadsync/uplopath [GET]](renter/renter-downloadsync-uplopath-get.md)
* [/renter/fuse [GET]](renter/renter-fuse-get.md)
* [/renter/fuse/mount [POST]](renter/renter-fuse-mount-post.md)
* [/renter/fuse/unmount [POST]](renter/renter-fuse-unmount-post.md)
* [/renter/recoveryscan [GET]](renter/renter-recoveryscan-get.md)
* [/renter/recoveryscan [POST]](renter/renter-recoveryscan-post.md)
* [/renter/rename/uplopath [POST]](renter/renter-rename-uplopath-post.md)
* [/renter/stream/uplopath [GET]](renter/renter-stream-uplopath-get.md)
* [/renter/upload/uploadpath [POST]](renter/renter-upload-uplopath-post.md)
* [/renter/uploadstream/uplopath [POST]](renter/renter-uploadstream-uplopath-post.md)
* [/renter/uploadready [GET]](renter/renter-uploadready-get.md)
* [/renter/uploads/pause [POST]](renter/renter-uploads-pause-post.md)
* [/renter/uploads/resume [POST]](renter/renter-uploads-resume-post.md)
* [/renter/validateuplopath/uplopath [POST]](renter/renter-validateuplopath-uplopath-post.md)
* [/renter/workers [GET]](renter/renter-workers-get.md)

## Transaction Pool
* [/tpool/confirmed/:id [GET]](transaction-pool/tpool-confirmed-id-get.md)
* [/tpool/fee [GET]](transaction-pool/tpool-fee-get.md)
* [/tpool/raw/:id [GET]](transaction-pool/tpool-raw-id-get.md)
* [/tpool/raw [POST]](transaction-pool/tpool-raw-post.md)
* [/tpool/transactions [GET]](transaction-pool/tpool-transactions-get.md)

## Wallet
* [/wallet [GET]](wallet/wallet-get.md)
* [/wallet/033x [POST]](wallet/wallet-033x-post.md)
* [/wallet/address [GET]](wallet/wallet-address-get.md)
* [/wallet/addresses [GET]](wallet/wallet-addresses-get.md)
* [/wallet/seedaddrs [GET]](wallet/wallet-seedaddrs-get.md)
* [/wallet/backup [GET]](wallet/wallet-backup-get.md)
* [/wallet/changepassword [POST]](wallet/wallet-changepassword-post.md)
* [/wallet/init [POST]](wallet/wallet-init-post.md)
* [/wallet/init/seed [POST]](wallet/wallet-init-seed-post.md)
* [/wallet/seed [POST]](wallet/wallet-seed-post.md)
* [/wallet/seeds [GET]](wallet/wallet-seeds-get.md)
* [/wallet/uplocoins [POST]](wallet/wallet-uplocoins-post.md)
* [/wallet/uplofunds [POST]](wallet/wallet-uplofunds-post.md)
* [/wallet/uplogkey [POST]](wallet/wallet-uplogkey-post.md)
* [/wallet/sign [POST]](wallet/wallet-sign-post.md)
* [/wallet/sweep/seed [POST]](wallet/wallet-sweep-seed-post.md)
* [/wallet/lock [POST]](wallet/wallet-lock-post.md)
* [/wallet/transaction/:id [GET]](wallet/wallet-transaction-id-get.md)
* [/wallet/transactions [GET]](wallet/wallet-transactions-get.md)
* [/wallet/transactions/:addr [GET]](wallet/wallet-transactions-addr-get.md)
* [/wallet/unlock [POST]](wallet/wallet-unlock-post.md)
* [/wallet/unlockconditions/:addr [GET]](wallet/wallet-unlockconditions-addr-get.md)
* [/wallet/unspent [GET]](wallet/wallet-unspent-get.md)
* [/wallet/verify/address/:addr [GET]](wallet/wallet-verify-address-addr-get.md)
* [/wallet/verifypassword [GET]](wallet/wallet-verifypassword-get.md)
* [/wallet/watch [GET]](wallet/wallet-watch-get.md)
* [/wallet/watch [POST]](wallet/wallet-watch-post.md)
