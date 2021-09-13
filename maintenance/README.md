




- old_dir_delete.sh

    $> old_dir_delete.sh {기준일} {지난일자카운트}

	 script 	
		!/bin/bash
		echo $1
		target_day=$(date -d "$1" "+%s")
		echo $target_day
		echo ----------------------
		for i in $(ls -d /home/deploy/test/*/); do
		    folder_date=`basename ${i%%/};`
		    echo $folder_date
		    f_day=$(date -d "$folder_date" "+%s")
		    echo $f_day
		    diff_date=`echo "($target_day - $f_day) / 86400"|bc`
		    echo $diff_date
		    if [ $diff_date -ge $2 ]
		    then
		      echo $2 지정한 날짜 값보다 작아서 삭제함:: $i
		      rm -rf $i;
		    fi
		
		done



- xxx.service

파일 생성 위치 

	/etc/systemd/system

서비스 등록 활성화

    sudo systemctl daemon-reload
	sudo systemctl enable tomcat
	sudo systemctl start tomcat