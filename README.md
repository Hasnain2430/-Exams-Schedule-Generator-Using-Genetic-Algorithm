# Exams-Schedule-Generator-Using-Genetic-Algorithm

A Python tool that generates optimized exam schedules using a custom Genetic Algorithm. It enforces hard constraints (e.g., no exam overlap, weekday-only exams, and invigilator availability) and optimizes soft constraints (e.g., student and teacher breaks). The algorithm uses techniques like roulette wheel selection, mutation, and crossover to evolve the solution over generations. It outputs a tabular timetable with fitness scores, making it ideal for scheduling in universities.

## Table of Contents
- [Overview](#overview)
- [Installation](#installation)
- [Dataset](#dataset)
- [Genetic Algorithm](#genetic-algorithm)
- [Hard and Soft Constraints](#hard-and-soft-constraints)
- [Usage](#usage)
- [Results](#results)
- [Contributing](#contributing)

## Overview
The tool uses a Genetic Algorithm to optimize exam schedules for a given set of courses, students, teachers, and available exam slots. The solution ensures that all courses have exams, no students or invigilators are double-booked, and breaks are scheduled as required. It adapts through a process of evolution, constantly improving the solution by selecting, crossing, and mutating chromosomes.

## Installation

To run this project, you'll need to install the following dependencies:

```bash
pip install pandas numpy
```

Ensure you have Python 3.7+ installed.

## Dataset

The project requires the following datasets in CSV format:
1. **Courses.csv**: Contains course codes and details.
2. **studentCourse.csv**: Maps students to the courses they are enrolled in.
3. **studentNames.csv**: Contains student names.
4. **teachers.csv**: Contains teacher names for invigilation.

Each file should be placed in the specified directory structure, as referenced in the code.

## Genetic Algorithm

The Genetic Algorithm implemented here is custom-built and includes the following components:
- **Chromosome Representation**: Each chromosome represents a possible exam schedule, with random generation of exam timings, days, and invigilators.
- **Fitness Calculation**: Fitness is calculated based on compliance with hard and soft constraints.
- **Roulette Wheel Selection**: Used to select parent chromosomes for crossover based on their fitness.
- **Crossover**: Columns of parent chromosomes are swapped at a random point.
- **Mutation**: Random changes to the exam day and start time, simulating natural genetic mutation.

## Hard and Soft Constraints

### Hard Constraints
The following must be strictly enforced:
1. An exam is scheduled for each course.
2. Students cannot have overlapping exams.
3. Exams are held only on weekdays.
4. Exam timings are restricted to 9 AM - 5 PM.
5. Invigilators cannot supervise multiple exams simultaneously.
6. Invigilators cannot have consecutive exam duties.

### Soft Constraints
These are optimized but can be adjusted:
1. All students and invigilators should have a break from 1 PM - 2 PM on Fridays.
2. Students should not have back-to-back exams.
3. MG courses should ideally be scheduled before CS courses.
4. A two-hour faculty meeting break should be incorporated.

## Usage

1. Open the script (`exams_schedule_generator.ipynb`) in a Jupyter Notebook or IDE.
2. Run the cells sequentially to execute the code, generate the population, and evolve the schedule over generations.
3. The algorithm will output the best-found schedule once it meets the target fitness score of 400, along with a breakdown of hard and soft constraint compliance.

## Results

The final output is an optimized exam schedule displayed in a tabular format, showing the day, course, room, start time, and invigilator. The console will also display the current generation, best solution, and soft/hard constraint fulfillment status.

## Contributing

Feel free to contribute to this project by creating pull requests, reporting issues, or suggesting new features.
