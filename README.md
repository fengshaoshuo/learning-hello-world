# learning-hello-world
I come from china,Although my English is poor.I want to learn more about Java.
public static void readCreateAfterFile() throws IOException {
		BufferedReader bReader = new BufferedReader(new FileReader(new File(COORDINATES_FILE)));
		BufferedWriter bWriter = new BufferedWriter(new FileWriter(new File(NUMBER_FILE)));
		// dataMap()方法将xlsx文件放到map中
		Map<String, String> dataMap = dataMap();
		Set<Entry<String, String>> entrySet = dataMap.entrySet();
		String temp = new String();
		String index1 = new String();
		String index2 = new String();
		String index3 = new String();
		// 创建数组
		String[] arr = null;
		List<String[]> list = new ArrayList<String[]>();// 创建list保存
		// 遍历读取的本地文件
		while ((temp = bReader.readLine()) != null) {
			arr = new String[3];
			String[] split = temp.split(",");
			index1 = split[0];
			index2 = split[1];
			index3 = split[2];
			// 遍历map，通过map的value得到key，将key放进数组中，将数组放进lists中
			for (Entry<String, String> entry : entrySet) {
				if (entry.getValue().equals(index1)) {
					arr[0] = entry.getKey();
				}
				if (entry.getValue().equals(index2)) {
					arr[1] = entry.getKey();
				}
				if (entry.getValue().equals(index3)) {
					arr[2] = entry.getKey();
				}
			}
			list.add(arr);
		}
		for (int i = 0; i < list.size(); i++) {
			String[] strings = list.get(i);
			String str = "[" + strings[0] + "," + strings[1] + "," + strings[2] + "]";
			bWriter.write(str + "\r\n");
			bWriter.flush();
		}
		bWriter.close();
		bReader.close();

		System.out.println("生成坐标编号的本地文件");
	}
