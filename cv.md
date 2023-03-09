# Aliaksei Sinitsyn
*********************************
## Personal informations
*  Minsk, Belarus
*  +375295531934
*  5531934@Gmail.Com

## Work experience
**************************
#### October 2021 - present
 __Middle 3D modeling developer__
* *Tools set development*
* *Minsk Tractor Works/ Minsk, Belarus*
* *Auto industry*

#### August 2018 - august 2020
__IT spectator service manager__
* *GRIP, SLA, CodSet, TEAP development. Development of documentation for the technical equipment of functional premises. Development of the registration form (PHP) to create the database of employees and templates for accreditation cards.*
* *2-nd European Games in Minsk/ Minsk, Belarus*
* *Multi sport games industry*

#### June 2012 - August 2018
__Junior Wordpress Developer__
* *Creating websites(WP)  itamada.com and radujterem.by. Website development from scratch, layout, expanding menu items, installing photo gallery, widgets, ratings, working with Google ad placement and analytics, monitoring traffic and creating a schedule for postings*
* *Freelancer/Minsk,Belarus*

*****************
## Code example

PHP OPP Interface
```
class FileStorage implements IStorage{
	protected static array $records = [];
	protected static int $ai = 0;
	protected static string $dbPath;
	protected function __construct(){}

	public static function getInstance(string $dbPath):self{
		self::$dbPath = $dbPath;
		if(file_exists(self::$dbPath)){
			$data = json_decode(file_get_contents(self::$dbPath), true);
			
			self::$records = $data['records'];

		
			self::$ai = $data['ai'];
		}
		return new self();
	}

	public function create(array $fields) : int{
		    $id = ++self::$ai;
			self::$records[$id] = $fields;
			$this->save();
			return self::$id;
	}

	public function get(int $id) : ?array{
		return self::$records[$id] ?? null;
	}

	public function remove(int $id) : bool{
		if(array_key_exists($id, self::$records)){
			unset(self::$records[$id]);
			$this->save();
			return true;
		}

		return false;
	}

	public function update(int $id, array $fields) : bool{
		if(array_key_exists($id, self::$records)){
			self::$records[$id] = $fields;
			$this->save();
			return true;
		}

		return false;
	}

	protected function save(){
		file_put_contents(self::$dbPath, json_encode([
			'records' => self::$records,
			'ai' => self::$ai
		]));
	}
}
```


